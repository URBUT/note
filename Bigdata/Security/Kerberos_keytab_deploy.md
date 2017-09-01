## Create and Deploy the Kerberos Principals and Keytab Files
---

### To create the Kerberos principals
```script
$ kadmin
```

```sh
$ addprinc -randkey hdfs/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey hdfs/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey hdfs/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey mapred/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey mapred/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey mapred/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey yarn/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey yarn/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey yarn/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey HTTP/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey HTTP/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey HTTP/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey hbase/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey hbase/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey hbase/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey hive/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey hive/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey hive/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey host/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey host/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey host/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey oozie/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey oozie/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey oozie/sbpdj03.sbp.com@SBP.COM

$ addprinc -randkey zookeeper/sbpdj01.sbp.com@SBP.COM
$ addprinc -randkey zookeeper/sbpdj02.sbp.com@SBP.COM
$ addprinc -randkey zookeeper/sbpdj03.sbp.com@SBP.COM
```

### To create the Kerberos keytab files

##### Create the *hdfs* keytab file (contain the hdfs principal and HTTP principal)
각 dir를 생성 (ex /engn001/sbp/security/keytab/sbpdj02, sbpdj03) 후
dir 내부로 들어가 각 호스트에 맞는 keytab 파일을 생성한다.

```
$ xst -norandkey -k hdfs.keytab hdfs/sbpdj03.sbp.com@SBP.COM host/sbpdj03.sbp.com@SBP.COM HTTP/sbpdj03.sbp.com@SBP.COM

$ xst -norandkey -k mapred.keytab mapred/sbpdj02.sbp.com@SBP.COM host/sbpdj02.sbp.com@SBP.COM HTTP/sbpdj02.sbp.com@SBP.COM

$ xst -norandkey -k yarn.keytab yarn/sbpdj02.sbp.com@SBP.COM host/sbpdj02.sbp.com@SBP.COM HTTP/sbpdj02.sbp.com@SBP.COM

$ xst -norandkey -k hbase.keytab hbase/sbpdj02.sbp.com@SBP.COM

$ xst -norandkey -k hive.keytab hive/sbpdj02.sbp.com@SBP.COM host/sbpdj02.sbp.com@SBP.COM HTTP/sbpdj02.sbp.com@SBP.COM

$ xst -norandkey -k oozie-http.keytab oozie/sbpdj02.sbp.com@SBP.COM HTTP/sbpdj02.sbp.com@SBP.COM

$ xst -norandkey -k zookeeper.keytab zookeeper/sbpdj02.sbp.com@SBP.COM
```
