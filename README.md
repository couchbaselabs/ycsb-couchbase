# Couchbase Driver for YCSB 2.0.0
This driver is a binding for the YCSB facilities to operate against a Couchbase Server cluster. It uses the official
Couchbase Java SDK (version 3.x) and provides a rich set of configuration options.

## Quickstart

### 1. Start Couchbase Server
You need to start a single node or a cluster to point the client at. Please see [http://couchbase.com](couchbase.com)
for more details and instructions.

### 2. Set up YCSB
You can either download the release zip and run it, or just clone from master.

```
curl -OLs https://github.com/mminichino/ycsb-couchbase/releases/download/2.0.0/ycsb-couchbase.zip
```
```
unzip ycsb-couchbase.zip
```
```
cd ycsb-couchbase
```
On Linux/macOS:
```
vi conf/db.properties
```
On Windows:
```
notepad conf\db.properties
```
On Linux macOS:
```
bin/run.sh
```
On Windows:
```
bin\run.bat
```

### 3. Run a specific test

```
bin/run.sh -w workloads/workloade
```

### Manual Mode

To just create the bucket:
```
./run_cb.sh -h cbnode-0000.domain.com -B
```

To just create the index:
```
./run_cb.sh -h cbnode-0000.domain.com -I
```

To run a data load:
```
./run_cb.sh -h cbnode-0000.domain.com -s -M -l -w a
```

To run a scenario:
```
./run_cb.sh -h cbnode-0000.domain.com -s -M -r -w a
```

To manually load data (without any script automation - i.e. if ```cbc``` isn't installed):
```
./run_cb.sh -h cbnode-0000.domain.com -s -Z -M -l -w a
```

To manually run a scenario (without any automation):
```
./run_cb.sh -h cbnode-0000.domain.com -s -Z -M -r -w a
```

## Capella
For Couchbase Capella (Couchbase hosted DBaaS) you will need to create a bucket named "ycsb" before you run the test(s).
This is because Capella database users do not have sufficient permissions to operate on buckets. You will also need to 
use SSL to connect. You can provide the name given on the Capella portal as the host. The helper utility will get the SRV 
records and extract a node name to use for the host parameter.

```
./run_cb.sh -h cb.abcdefg.cloud.couchbase.com -s -u dbuser -p password 
```

## Configuration Options
Since no setup is the same and the goal of YCSB is to deliver realistic benchmarks, here are some setups that you can
tune. Note that if you need more flexibility (let's say a custom transcoder), you still need to extend this driver and
implement the facilities on your own.

You can set the following properties (with the default settings applied):

- couchbase.host=127.0.0.1: The hostname from one server.
- couchbase.bucket=ycsb: The bucket name to use.
- couchbase.scope=_default: The scope to use.
- couchbase.collection=_default: The collection to use.
- couchbase.password=: The password of the bucket.
- couchbase.durability=: Durability level to use.
- couchbase.persistTo=0: Persistence durability requirement
- couchbase.replicateTo=0: Replication durability requirement
- couchbase.upsert=false: Use upsert instead of insert or replace.
- couchbase.adhoc=false: If set to true, prepared statements are not used.
- couchbase.maxParallelism=1: The server parallelism for all n1ql queries.
- couchbase.kvEndpoints=1: The number of KV sockets to open per server.
- couchbase.sslMode=false: Set to ```true``` to use SSL to connect to the cluster.
- couchbase.sslNoVerify=true: Set to ```false``` to check the SSL server certificate.
- couchbase.certificateFile=: Path to file containing certificates to trust.
- couchbase.kvTimeout=2000: KV operation timeout (milliseconds)
- couchbase.queryTimeout=14000: Query timeout (milliseconds)
- couchbase.mode=DEFAULT: Test operating mode (DEFAULT or ARRAY).
- couchbase.ttlSeconds=0: Set document expiration (TTL) in seconds.
