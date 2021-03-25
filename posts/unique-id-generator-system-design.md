---
title: Key Points regarding Unique ID generator in distributed systems
created: 2021-03-25T02:30:00+05:30
updated: 2021-03-25T02:30:00+05:30
author: ashishdoneriya
description: Unique ID geneator system design key points to remember
permalink: /unique-id-generator-system-design.html
categories:
  - system-design
tags:
  - snowflake
  - uuid
---

## Key Points
* MySQL auto increment is not sufficient for distributed systems because it is not large enough & would be very challenging generating unique ids across multiple databases with minimal delay;

* Our requirement is the ids should be unique, sortable, max 64 bit (8 bytes ie. could fit in long data type in Java).

There are three ways that could be possible -

### UUID
* UUID is 128 bit.
* It has very low probability of collusion.
* It could be generated without coordinated servers.
* It has drawback that is the ids could be non numeric.
* Since our requirement is 64 bits, therefore UUIDs won't be able to satisfy our requirements

### Ticket Server
* [Flickr](https://code.flickr.net/2010/02/08/ticket-servers-distributed-unique-primary-keys-on-the-cheap/) developed this technique.
* There is a dedicated mysql server database which is used to generate keys.
* All the other servers hit mysql to get the unique keys.
* This approach has drawback. It has single point of failure. In case of that single mysql server machine goes down, the entire system would fail.
* The webservers would hit the below sql command to get the unique key.
```sql
REPLACE INTO Tickets64 (stub) VALUES ('a');SELECT id from Tickets64;
```
The table creating syntax is -
```sql
CREATE TABLE `Tickets64` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `stub` char(1) NOT NULL DEFAULT '',
  PRIMARY KEY (`id`),
  UNIQUE KEY `stub` (`stub`)
) ENGINE=InnoDB
```

### Twitter Snowflake
Twitter snowflake IDs are 64-bit. In this approach the ID is divided into multiple parts - 
* 1 bit - **reserved**
* 41 bit - **for storing timestamp** epoch. Instead of storing milliseconds since 1 January 1970, we will start from 4 Nov 2010 01:42:54 UTC (1288834974657) that is twitter snowflake default epoch.
* 5 bit - **data center id**. Maximum 2^5 = 32 datacenters.
* 5 bit - **machine id**. Maximum 2^5=32 machines per datacenter. This means not every webserver could generate its own key individualy. There has to be a dedicated id generator (distributed key generator).
* 12 bits - **sequence number**. For every request the number gets increased. After every millisecond the number resets to 0.

This id generator would work for around 70 years.

