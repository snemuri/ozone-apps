# ozone-apps

## Ozone as default filesystem


HDFS

In core-site.xml, Add:
fs.defaultFS=o3fs://bucket.hdfsonozone/
fs.AbstractFileSystem.o3fs.impl=org.apache.hadoop.fs.ozone.OzFs
fs.o3fs.impl=org.apache.hadoop.fs.ozone.OzoneFileSystem

In hadoop-env.sh, Add:

`export HADOOP_CLASSPATH=$HADOOP_CLASSPATH:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-0.4.0-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-proto-0.4.0-f283ffa-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-thirdparty-misc-0.2.0.jar:/opt/ozone-0.4.0-SNAPSHOT/etc/hadoop:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/bcprov-jdk15on-1.60.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-lib-0.4.0-SNAPSHOT.jar`


YARN

In yarn-site.xml, update:

`yarn.application.classpath=$HADOOP_CONF_DIR,{{hadoop_home}}/*,{{hadoop_home}}/lib/*,{{stack_root}}/current/hadoop-hdfs-client/*,{{stack_root}}/current/hadoop-hdfs-client/lib/*,{{stack_root}}/current/hadoop-yarn-client/*,{{stack_root}}/current/hadoop-yarn-client/lib/*,/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-0.4.0-SNAPSHOT.jar,/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-proto-0.4.0-f283ffa-SNAPSHOT.jar,/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-thirdparty-misc-0.2.0.jar,/opt/ozone-0.4.0-SNAPSHOT/etc/hadoop,/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/bcprov-jdk15on-1.60.jar,/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-lib-0.4.0-SNAPSHOT.jar`


MR

`$PWD/mr-framework/hadoop/share/hadoop/mapreduce/*:$PWD/mr-framework/hadoop/share/hadoop/mapreduce/lib/*:$PWD/mr-framework/hadoop/share/hadoop/common/*:$PWD/mr-framework/hadoop/share/hadoop/common/lib/*:$PWD/mr-framework/hadoop/share/hadoop/yarn/*:$PWD/mr-framework/hadoop/share/hadoop/yarn/lib/*:$PWD/mr-framework/hadoop/share/hadoop/hdfs/*:$PWD/mr-framework/hadoop/share/hadoop/hdfs/lib/*:$PWD/mr-framework/hadoop/share/hadoop/tools/lib/*:/usr/hdp/${hdp.version}/hadoop/lib/hadoop-lzo-0.6.0.${hdp.version}.jar:/etc/hadoop/conf/secure:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-0.4.0-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-proto-0.4.0-f283ffa-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-thirdparty-misc-0.2.0.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/bcprov-jdk15on-1.60.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-lib-0.4.0-SNAPSHOT.jar`


SPARK
In spark2-defaults.conf

`spark.driver.extraClassPath=/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-0.4.0-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-proto-0.4.0-f283ffa-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-thirdparty-misc-0.2.0.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/bcprov-jdk15on-1.60.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-lib-0.4.0-SNAPSHOT.jar`

`spark.executor.extraClassPath=/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-0.4.0-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-proto-0.4.0-f283ffa-SNAPSHOT.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/ratis-thirdparty-misc-0.2.0.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/bcprov-jdk15on-1.60.jar:/opt/ozone-0.4.0-SNAPSHOT/share/ozone/lib/hadoop-ozone-filesystem-lib-0.4.0-SNAPSHOT.jar`

`spark.hadoop.fs.AbstractFileSystem.o3fs.impl=org.apache.hadoop.fs.ozone.OzFs`


Hive

fs.defaultFS=o3fs://bucket.hdfsonozone/

