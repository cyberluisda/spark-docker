# spark-docker

Project with docker definitions of spark images

# Versions:

* latest,1.6.3: spark 2.1 image
* connectors-1.6.3: spark 1.6.3 with some libraries added:
  * org: `spark.jobserver`, name: `job-server-api_2.10`, version: `0.6.2`
  * org: `spark.jobserver`, name: `job-server-extras_2.10`, version: `0.6.2`
  * org: `io.snappydata`, name: `snappydata-store-client`, version: `1.5.0`
  * org: `com.databricks`, name: `spark-xml_2.10`, version: `0.3.4`

## Which connectors

Libraries added are usefull to make integration tests with snappy and job-server
using `spark-shell`.

We have not any _Class not found exception_ when launch partial jobs that have
this depenencies.

But really **does not** start any other componenet (neither
spark-jobserver nor snappydata-server).
