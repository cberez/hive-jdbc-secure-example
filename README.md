# Hive JDBC secure example

Simple example project to write to a secure hive with kerberos.
Developped and tested on CDH 5.7.1.

## Build

```bash
mvn package
```

## Parameters

```bash
 -h,--help                    Display this help
 -hp,--hive-principal <arg>   The principal for the HiveServer2 node (mandatory)
 -kc,--krb-conf <arg>         Path to krb5.conf
 -kt,--keytab <arg>           The app's keytab (mandatory)
 -p,--port <arg>              The HiveServer2 port (default: 10000)
 -pr,--principal <arg>        The app principal (mandatory)
 -s,--server <arg>            The HiveServer2 address (default: localhost)
```

If you run on the HiveServer2's server, you need to set the `hive-principal`,  `principal` and `keytab`.

If you run it from an external server, add the `krb-conf` and `server` parameters.

So it would look like :

```bash
# On HS2
java -jar /path/to/HiveJDBCWriter-1.0.jar \
  --hive-principal "hive/<hiveserver2_host>@REALM"
  --principal "my_app_princ@REALM"
  --keytab "/path/to/my_app_princ.keytab"
  
# From an external serv
java -jar /path/to/HiveJDBCWriter-1.0.jar \
  --hive-principal "hive/<hiveserver2_host>@REALM"
  --principal "my_app_princ@REALM"
  --keytab "/path/to/my_app_princ.keytab"
  --krb-conf "/path/to/krb5.conf"
  --server "<hiveserver2_host>"
  --port 10000
```
