## Steps to integrate nifi with Ozone

- Update the nifi-hadoop-libraries-nar (/usr/hdf/current/nifi/lib/nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar) with Ozone jars. 

 ```
 /usr/jdk64/jdk1.8.0_112/bin/jar uf nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar META-INF/bundled-dependencies/hadoop-ozone-filesystem-0.4.0-SNAPSHOT.jar
 /usr/jdk64/jdk1.8.0_112/bin/jar uf nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar META-INF/bundled-dependencies/hadoop-ozone-filesystem-lib-0.4.0-SNAPSHOT.jar
 /usr/jdk64/jdk1.8.0_112/bin/jar uf nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar META-INF/bundled-dependencies/ratis-thirdparty-misc-0.2.0.jar
 /usr/jdk64/jdk1.8.0_112/bin/jar uf nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar META-INF/bundled-dependencies/ratis-proto-0.4.0-a8c4ca0-SNAPSHOT.jar
 /usr/jdk64/jdk1.8.0_112/bin/jar uf nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar META-INF/bundled-dependencies/bcprov-jdk15on-1.60.jar
 /usr/jdk64/jdk1.8.0_112/bin/jar uf nifi-hadoop-libraries-nar-1.8.0.3.3.1.0-10.nar META-INF/bundled-dependencies/hadoop-common-3.1.1.3.1.0.0-78.jar
 ```


- Import the template [nifi-ozone.xml](https://github.com/snemuri/ozone-apps/blob/master/nifi%20integration/nifi-ozone.xml) into Nifi.

- Copy the core-site.xml,hdfs-site.xml & ozone-site.xml into a Nifi node (default file system should contain the o3fs url) and
configure it in PutHDFS processor. Eg: `/opt/hadoop-ozone-conf/core-site.xml,/opt/hadoop-ozone-conf/hdfs-site.xml,/opt/hadoop-ozone-conf/ozone-site.xml`

- Start the processors and nifi should be writing the data to `/nifi-ozone-1` path. 
