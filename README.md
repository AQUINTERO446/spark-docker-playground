# spark-docker-playground
Playground based on [Spark Docker](https://github.com/big-data-europe/docker-spark)

Make sure to fill in the `INIT_DAEMON_STEP` as configured in your pipeline.
## Running Docker containers without the init daemon
### Spark Master
To start a Spark master:

    docker run --name spark-master -h spark-master -d bde2020/spark-master:3.3.0-hadoop3.3

### Spark Worker
To start a Spark worker:

    docker run --name spark-worker-1 --link spark-master:spark-master -d bde2020/spark-worker:3.3.0-hadoop3.3

## Runing Docker Compose
docker-compose up -d
### Execute container with worker 1

```sh
docker exec -it spark-worker-1 bash
```

### Python examples

* Run pyspark CLI:
```sh
./spark/bin/pyspark
```
*  Execute a file
```sh
cd home/python/example
./../../../spark/bin/spark-submit example.py data.csv
```

## Launch a Spark application
Building and running your Spark application on top of the Spark cluster is as simple as extending a template Docker image. Check the template's README for further documentation.
* [Maven template](https://github.com/big-data-europe/docker-spark/tree/master/template/maven)
* [Python template](https://github.com/big-data-europe/docker-spark/tree/master/template/python)
* [Sbt template](https://github.com/big-data-europe/docker-spark/tree/master/template/sbt)