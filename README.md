# spark-docker

Project with docker definitions of spark images

# Versions:

* latest,2.1: spark 2.1.1 image
* connectors-2.1: spark 2.1 with some libraries added:
  * `spark-streaming-kafka-0-10_2.11`, version `2.1.0`
  * `spark-cassandra-connector-unshaded_2.11`, version `2.0.0-M3`

## Removed from previous versions

  * `elasticsearch-spark-20_2.11`, version: `5.1.1`. Removed for
    incompatibility with spark `2.1.1` reason.
