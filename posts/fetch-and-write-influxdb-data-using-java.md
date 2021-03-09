---
title: How to fetch and write influxdb data using java
created: 2016-05-26T15:36:02+05:30
author: ashishdoneriya
description: Steps to write data into influxdb (influx time series database) and also fetch data from it very easily.
permalink: /fetch-and-write-influxdb-data-using-java.html
categories:
  - database
  - java
tags:
  - influxdb
  - java
updated: 2016-05-26T15:36:02+05:30
---

[Influx](/influxdb-tutorial.html) time series database is a platform for storing, collecting, visualizing and managing time-series data.

There is already official java api in maven and github. But I have created an api for influxdb in [Github](https://github.com/ashishdoneriya/influxdb-java). From that we could fetch and write to database very easily. To use that api [download jar](https://github.com/ashishdoneriya/influxdb-java/releases/download/3.0.1/influxdb-3.0.1.jar). You can also add dependency in your project using [JitPack](https://jitpack.io/#ashishdoneriya/influxdb-java/3.0.1).

In Influxdb we call tables as measurements and columns as fields. So let's start.

Steps for writing data.

1. First create configuration. 
```java
Configuration configuration = new Configuration("localhost", "8086", "root", "root", "mydb");
```


The parameters above are for host, port, user and password respectively.

* Now to write data create Object of `DataWriter` class. 
```java
DataWriter writer = new DataWriter(configuration);
```

We have to pass configuration.

* Now we set measurement name ( or you can say table name). 
```java
writer.setMeasurement("sampleMeasurement1");
```


* Set time unit ie what time format do you want to use. 
```java
writer.setTimeUnit(TimeUnit.SECONDS);
```


Supported formats in influxdb are `HOURS`, `MINUTES`, `SECONDS`, `MILLISECONDS`, `MICROSECONDS` and `NANOSECONDS`.

* Now set time 
```java
writer.setTime(System.currentTimeMillis() / 1000);
```


**Note :** In here we defined time in seconds because in step we set the time in seconds.

* Add fields (or you can say columns).

```java

writer.addField("field1", 12212);		// Integer value
writer.addField("field2", 22.44);		// Double value
writer.addField("field3", "thisIsString");	// String value
writer.addField("field4", false);		// boolean value

```


In influxdb we don't need to define table (measurements) or columns (fields) and its datatype. Influxdb will create that automatically as we insert data. We just need to define database.

* Add Tags 
```java
writer.addTag("hostname", "server001");
writer.addTag("disk_type", "SSD");

```


* To write the above data into database use 
```java
writer.writeData();
```


It will then insert the data into influxdb.

* We can use the same writer to add more data into fields. 
```java
writer.addField("field1", 112);
writer.addField("field1", 21.44);
writer.addField("field1", "thisIsString1");
writer.addField("field1", true);
// Influxdb saves one point at one time. Therefore we have to add another point at another time.
writer.setTime(System.currentTimeMillis() / 1000 + 1);
writer.addTag("disk_type", "HDD");
writer.writeData();
```


**Note : 1.** Make sure put the same type of data into particular column.ie. in step 6. datatype of column1 and column2 are integer and decimal type. Next time whenever we put data in these columns datatype should also be integer and decimal type afterthat.  
**2.** Influxdb saves one point at one time. To add another point at same time we can use tags otherwise it will override the previous point.

Steps to read data from Influxdb.

1. Create configuration. 
```java
Configuration configuration = new Configuration("localhost", "8086", "root", "root", "mydb");
```


2. Create object of `Query` class. 
```java
Query query = new Query();
```


3. To set the measuremen name. 
```java
query.setMeasurement("sampleMeasurement1");
```


If we want to set multiple measurements then.


```java
List&lt;String> list = new ArrayList&lt;String>();
list.add("sampleMeasurement1");
list.add("sampleMeasurement2");
query.setMeasurements(list);
```


1. To set fields whose values we want to fetch. 
```java
query.addField("field1");
query.addField("field2");
```


It will fetch all fields by default, if not specified as above. (like select * from).

* If you want to set time limit like fetch data of last 1 hour. 
```java
query.setDuration("1h");
```


or fetch data for last 120 seconds.

```java
query.setDuration("120s");
```


Supported format are `d`, `h`, `m`, `s`.

* d = days
* h = hours
* m = minutes
* s = seconds

If you want to put the data range then use.

```java
query.setRange(new Date(2012, 12, 31), new Date())
```


* If you want to set aggregate function then 
```java
query.setAggregateFunction(AggregateFunction.MEAN);
```


Supported functions in influxdb are `COUNT`, `MIN`, `MAX`, `MEAN`, `MODE`, `MEDIAN`, `DISTINCT`, `SUM`, `STDDEV`, `FIRST`, `LAST`, `DIFFERENCE` and `NOFUNCTION`.

* To set group by time like for 1 minute. 
```java
 query.setGroupByTime("1m");
```


* To limit the number of rows. 
```java
query.setLimit(1000);
```


* When we use 'group by' in query, then influxdb will return NULL for a time if their is no value found in that range (ie. 1m as defined above). So if you want to replace that NULL value with something like number then use 
```java
query.fillNullValues("0");
```


It will replace all null values with 0.

* Now create object of `DataReader` class and fetch the result. 
```java
DataReader dataReader = new DataReader(query, configuration);
ResultSet resultSet = dataReader.getResult();
System.out.println(resultSet);
```


The resultSet contains the result.
