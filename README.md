# spark-flamegraph

spark-submit wrapper that generates Flame Graph.

![Flame Graph Example](flamegraph.png)

## Supported Systems

 * Linux

## Prerequisites

The following commands must be present:

 * perl
 * python2.7
 * pip

## Running

```bash
wget -O /usr/local/bin/spark-submit-flamegraph \
  https://raw.githubusercontent.com/spektom/spark-flamegraph/master/spark-submit-flamegraph

chmod +x /usr/local/bin/spark-submit-flamegraph
```

Use the `spark-submit-flamegraph` as a replacement for the `spark-submit` command.

## Details

The script does the following operations to make profiling Spark applications as easy as possible:

  * Downloads InfluxDB, and starts it on some random port.
  * Starts Spark application using original `spark-submit` command, with the statsd profiler Jar in its classpath and with the configuration that tells it to report statistics back to the InfluxDB instance.
  * After running Spark application, queries all the reported metrics from the InfluxDB instance.
  * Run a script that generates the .SVG file.
  * Stops the InfluxDB instance.

