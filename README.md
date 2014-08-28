# SparkOnHBase
## Overview
This is a simple reusable lib for working with HBase with Spark


##Functionality
Current functionality supports the following functions

* bulkPut
* bulkDelete
* bulkIncrement
* bulkGet
* bulkCheckAndPut
* bulkCheckAndDelete
* foreachPartition (with HConnection)
* mapPartition (with HConnection)
* hbaseRDD (HBaseInputFormat)
* Java APIs
* Java Examples
* Java Unit Tests

##Near Future
* More unit test
* More Examples
* Python APIs
* Python Examples
* Python Unit Test

##Far Future

* Partitioned Bulk Put/Mutation
* Sorted Partitioned Bulk Get
* Spark implementation of HBase bulkLoad
* Spark implementation of HBase copyTable


##Build
just mvn clean package

##CDH setup
Testing was done on CDH 5.0.2

Just put hbase-protocol-0.96.1.1-cdh5.0.2.jar in /opt/cloudera/parcels/CDH-5.0.2-1.cdh5.0.2.p0.13/lib/spark/assembly/lib/ and bunced

/opt/cloudera/parcels/CDH-5.1.0-1.cdh5.1.0.p0.53/lib/spark/assembly/lib

##Examples
SparkOnHBase comes with a number of examples.  Here is the Cli commands to try them out.  These work with a table named 't1' and columnfmaily 'c'

create 't1', 'c'

export HADOOP_CLASSPATH=/opt/cloudera/parcels/CDH/lib/hbase/lib/*:/opt/cloudera/parcels/CDH/lib/hbase/lib/hbase-protocol-0.98.1-cdh5.1.0.jar:/etc/hbase/conf

spark-submit --jars /opt/cloudera/parcels/CDH/lib/zookeeper/zookeeper-3.4.5-cdh5.1.0.jar,/opt/cloudera/parcels/CDH/lib/hbase/lib/guava-12.0.1.jar,/opt/cloudera/parcels/CDH/lib/hbase/lib/protobuf-java-2.5.0.jar,/opt/cloudera/parcels/CDH/lib/hbase/hbase-protocol.jar,/opt/cloudera/parcels/CDH/lib/hbase/hbase-client.jar,/opt/cloudera/parcels/CDH/lib/hbase/hbase-common.jar,/opt/cloudera/parcels/CDH/lib/hbase/hbase-hadoop2-compat.jar,/opt/cloudera/parcels/CDH/lib/hbase/hbase-hadoop-compat.jar,/opt/cloudera/parcels/CDH/lib/hbase/hbase-server.jar,/opt/cloudera/parcels/CDH/lib/hbase/lib/htrace-core.jar --class org.apache.spark.hbase.example.HBaseBulkPutExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --driver-java-options -Dspark.executor.extraClassPath=/opt/cloudera/parcels/CDH/lib/hbase/lib/* SparkHBase.jar x  t1 c

* java -cp SparkHBase.jar spark.hbase.example.HBaseBulkPutTimestampExample spark://{spark.master.host}:7077  t1 c
* java -cp SparkHBase.jar spark.hbase.example.HBaseBulkGetExample spark://{spark.master.host}:7077  t1 c
* java -cp SparkHBase.jar spark.hbase.example.HBaseBulkIncrementsExample spark://{spark.master.host}:7077  t1 c
* java -cp SparkHBase.jar spark.hbase.example.HBaseBulkPutExample spark://{spark.master.host}:7077  t1 c
* java -cp SparkHBase.jar spark.hbase.example.HBaseBulkDeletesExample spark://{spark.master.host}:7077 t1 c
* java -cp SparkHBase.jar spark.hbase.example.HBaseDistributedScanExample spark://tedmalaska-exp-b-1.ent.cloudera.com:7077 t1 c

sbt/sbt assembly 'test-only org.apache.spark.hbase*'


