# msys-apache-drill-0.7.0
apache drill 0.7.0 for windows with msys/mingw

this version of apache drill runs with following applications.
* hadoop 2.6.0
* hive 0.12.0


## how to build
download apache drill 0.7.0 source from git or apache archives.

```
patch -u -p1 < ../apache-drill-0.7.0-2.6.0-0.12.0-src-0002r.patch
```

copy 'hadoop-winutils-2.6.0.zip' binary file to distribution/src/lib folder.

```
mkdir distribution/src/lib
cp hadoop-winutils-2.6.0.zip distribution/src/lib
```

here, run maven.

```
mvn clean install -DskipTests
```


## how to run
run 'sqlline' command after looking into 'conf/drill-override.conf' file.

```
bin/sqlline
```
connect drillbit.

```
> !connect jdbc:drill:zk=local
```

then, open http://localhost:8047/ in your browser.

## troubleshooting
if drill got hang or exception happen, restart 'sqlline' after deleting 'c:\tmp\drill' folder.
some query for hive may cause an exception due to hive metastore implement issue.



## license
depends on original source.
