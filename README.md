## sbt project compiled with Scala 3

### Usage

This is a normal sbt project. You can compile code with `sbt compile`, run it with `sbt run`, and `sbt console` will start a Scala 3 REPL.

For more information on the sbt-dotty plugin, see the
[scala3-example-project](https://github.com/scala/scala3-example-project/blob/main/README.md).

### How to configure tsurugi.int

```
[sql]
    scan_default_parallel=2
    dev_rtx_parallel_scan=true
```

For two parallel executions, set scan_default_parallel=2 and dev_rtx_parallel_scan=true.
For non-parallel execution, set scan_default_parallel=1.
When the parallel count is not specified:

If dev_rtx_parallel_scan is set to true, the sticky flag will be off.
If dev_rtx_parallel_scan is set to false, the sticky flag will be on (default behavior).


### Parameter

#### Columncount

```
private val Columncount = 10_000_000 (src/main/scala/Main.scala)
```

Columncount represents the number of columns in the table.

### SQL

```
tgsql  -c ipc://tsurugi
tgsql> begin read only;
tgsql> select count(*) from test_table;
tgsql> commit;
tgsql> \exit
```
