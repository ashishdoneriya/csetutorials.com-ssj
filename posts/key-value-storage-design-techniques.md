---
title: Key Value Database Design and Techniques
created: 2021-03-23T23:14:21+05:30
updated: 2021-03-23T23:14:21+05:30
author: ashishdoneriya
description: Essential points to consider while designing key-value storage or database.
permalink: /key-value-storage-design-techniques.html
categories:
  - system-design
tags:
  - key-value-database
---

* It is a non-relational database. The key must be unique, can be plain text or hashed values. The value can be directly fetched through the key.

## Requirements

* The size of a key value pair is small ie. less than 10 KB.
* **Big Data :** It should be able to store very large amount of data (bigdata).
* **High Availability :** The system should repond to queries even in case of failures.
* **High Scalability :** The system should be able to scale according to the data and the traffic.
* Latency should be very low.

## Architecture

Since bigdata cannot be stored in a single machine, therefore we'll need multiple machines (nodes).

```text
                           ____________________________________
                           |                                   |
--------Request-------->   | [Node 1]  [Node 4]                |
--------Request-------->   | [Node 2]  [Node 5] .. .. [Node N] |
--------Request-------->   | [Node 3]  [Node 6]                |
                           |___________________________________|
                                  Multiple Nodes acting as
                                      a Single System
                                    (Distributed System)

```

There are various problems that we have to solve like -

* How to store key value in these nodes?
* How to fetch value corresponding to a particular node?
* How to replicate data?
* How to handle temporary and permanent failures?

### How to store data?

Steps to fetch the value for a key -

1. First of all we will use [Consistent Hashing](/consistent-hashing-design-techniques.html) technique to identify which key to store in which node or retrieve the value from which node.
2. We will use [SSTable technique](/sstable-architecture) to store the data in the individual node.

### How to fetch data?

We'll use the same concepts Consistent Hashing & SSTable to fetch value for a key.

### How to replicate data?

For replicating a key-value, we'll fetch next 2 (or 3, depending on replication factor / number of copies) **distinct server nodes from the hash ring** and save the copies into these nodes. It would be much better if the selected nodes would be of another rack or data center.

### How to handle temporary and permanent failures?

The nodes will use gossip protocol to communicate with each other. Using gossip protocol the nodes would get to know about each other's health. The every node in the cluster(distributed system) would know about every other node.

#### Handling temporary failures

There are two things that we could do in case of temporary failure. First is block all requests for that node which is not good. The second is continue to allow read and write operations using the next replicated node. That nodes would handle all read and write requests for the failed node. When failed node becomes active again then the replicated node would push back the changes in the original node.

#### Handling permanent failures

In case of permanent failure, the replicated node would continue to serve the keys.



