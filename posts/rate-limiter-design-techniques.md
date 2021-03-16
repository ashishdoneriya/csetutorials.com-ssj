---
title: Rate Limiter Design And Techniques
created: 2021-03-14T21:14:21+05:30
author: ashishdoneriya
description: Points regarding rate limiter designing techniques.
permalink: /rate-limiter-design-techniques.html
categories:
  - system-design
tags:
  - redis
  - rate-limiter
updated: 2021-03-14T21:14:21+05:30
---

Rate Limiting is a very vast topic. It depends on what type of rate limiter you want, what are your requirements. First lets assume there is a lot of traffic coming every second or minute. So we will do all the calculations according to the rate limiter.

**NOTE :** There should be minimal impact of rate limiter on apis latency.

## How to limit the traffic?

To put a control on traffic or a user who is sending a lot of requests, we have to put a middleware (rate limiter) between the internet traffic (ie. client) and the api servers. This rate limiter will decide whether a request should be allowed to hit the api servers or not based on client' ip address or client's details.

### From where does the rate limiter fetch the rule?

Lets say the rules for every user is stored in a database (RDBMS, NoSQL etc.). The data in the database is stored in the disk and the rate limiter is reading the rules from the database. Any request that comes to the rate limiter, it reads the rules from the database every time which is very slow as we know that reading the data from the disk is very slow.

But if we use some inmemory database like redis for reading the rules then the speed would become much faster. Therefore we'll store rules in inmemory database for faster access (and to reduce latency).

There'll be some worker nodes also who will update the rules on the inmemory database.

### What would happen when the rate limiter rejects the request?
When the user/client exceets his/her quota, the rate limiter sends 429 http error code to notify the user that there are too many request he's sending. The rate limiter also sends other info along with 429 code like when can the client again send the request, how many request it can send in a particular period of time.

## How actually rate limiter works?

There are various types of rate limiter techniques.

1. Token Bucket
2. Leaking Bucket
3. Fixed Window counter
4. Sliding window log
5. Sliding Window counter

### Token Bucket
* There is a bucket filled with tokens.
* When a request comes, it takes one token and proceeds.
* If there is no token in the bucket the request would get dropped.
* At regular interval the bucket gets refill.
* There is an overhead of refilling the bucket

### Leaking Bucket
* In leaking bucket there is a queue (bucket).
* All the requests go through that queue.
* The requests in the queue get processed at a fixed rate.
* If a request comes in and the queue is full then the request will be dropped.
* It is suitable for usecases that a stable outflow rate is needed.
* A Burst of traffic fills up the queue with old requests, and if they are not processed in time, recent requests will be rate limited.
* It allows sudden burst of traffic.

### Fixed Window Counter Algorithm
* A counter is maintained for a fixed interval.
* Every request that comes up increase the counter for that interval.
* If the counter value exceeds the max rate then the request will be dropped.
* There could be sudden burst of traffic at the edge of the window in this algorithm.

### Sliding window log algorithm
* This algorithm solves the problem of sudden spike in traffic at the edge of windows.
* In this algorithm we maintain the timestamp of each incoming request.
* When a request arrives then first outdated timestamps will be removed.
* After that the current timestamp will be added.
* Then all the log entries will be counted. If the total log entries is less than the rate then the request would be allowed otherwise it would be dropped.
* This algorithm consumes a lot of memory because even if a request is rejected, its timestamp might still be stored in memory.

### Sliding window counter algorithm
It is hybrid algorithm  that combines the fixed window counter and sliding window log. Lets say the rate limiter allows 7 requests in a minutes. And there are 5 requests in the previous minutes & 3 in the current minute. For a new request that arrives at a 30% position in the current minute, the number of requests in the rolling window is calculated using the following formula.
* Requests in current window + requests in the previous window * overlap percentage of the rolling window and previous window.
* Using this formula we get 3 + 5 * 0.7% = 6.5 = 6.
Since the rate limiter allows a maxium of 7 requests per minutes, the current request can go through.
This algo is memory efficient. But it only works for not-so-strict look back window. The problem is not so bad as it seems. According to an experiment by cloudflare only 0.003% of requests are wrongly allowed or rate limited among 400 million requests.


### Sliding window log algorithm implementations

#### Problem Detail : Max 500 requests in last 1 hour
Example : [https://github.com/peterkhayes/rolling-rate-limiter](https://github.com/peterkhayes/rolling-rate-limiter)
1. We'll use redis for cache.
2. **In redis there is a feature using which we can execute a set of operations atomically so as to prevent race condition. We get the output of the commands after all the commands get executed.**
3. We'll used sorted set in redis to store timestamps.
4. Now we will execute the steps from 5 to 7 atomically (as far as I understood we canot add an `if condition` in these steps)
5. Delete all timestamps before the interval.
6. Add the current timestamp.
7. Get the total elements currently in the set.
8. If the total elements is less than the applied rate then the request can proceed further otherwise it will be dropped.

#### Problem Detail : Max 10 requests per minute and there should be a gap of 2 second between each request.

[https://engineering.classdojo.com/blog/2015/02/06/rolling-rate-limiter/](https://engineering.classdojo.com/blog/2015/02/06/rolling-rate-limiter/)

1. Each user has a sorted set associated with them.
2. Executed the below steps from 3 to 5 atomically (we will be able to read the output only after execution of all the steps.)
3. When a request arrives, drop all elements of the set which occured before a minute ago.
4. Fetch all elements of the set.
5. Add the current timestamp to the set.
6. Count all the elements in the set when all operations are completed. If it exceeds the limit, we would drop the request.
7. Fetch the latest timestamp with the current timestamp. If they are too close ( < 2 seconds) then we would drop the request.

We can perform atomic operations in redis using `MULTI` command.

There is a drawback in this approach. We have to save the timestamps of the dropped requests also. Lets say there are 100 requests from client within a second then only 1 request would be allowed and the rest 99 requests would be dropped. But ever after two seconds these dropped requests' timestamps won't be removed from the sorted set. So all requests will be dropped untill the completion of 10 minutes.
Suppose what would happen if the duration would be of 1 hour instead of 10 minutes, then the user won't be able to access the apis for whole 1 hour. But it has its own advantage. We can penalize that type of users who try to spam.

