DB Replication
==============
* Master DB : 웹 서버로부터 CRUD Event 발생 시에 Binary Log를 생성하여 Slave로 전달
* Slave DB : Master DB로부터 받은 Binary Log를 전달받아 데이터를 반영

DB Replication 주의 사항
======================
1. 버전 문제 - DB 버전을 동일하게 맞추는 것을 권장 / 혹은 Slave가 Master의 상위 버전
2. DB 가동 순서 - Master 다음 Slave 순으로 구동

Master Replication Configuration
================================
1) DB 생성 - create database repl_db default character set utf8;
2) 계정 생성 - create user user1@'%' identified by 'password';
3) 권한 부여 - grant all privilages on repl_db.* to user1@'%' identified by 'password';
4) replication 계정 생성 - grant replication slave on *.* to 'repl_user'@'%' identified by 'password';

Masyer MySQL Configuration
===========================
vi /etc/my.cnf</br>
[mysqld]</br>
log-bin=mysql-bin</br>
server-id=1</br>

Master Server 정보 확인
=====================
* mysql > show master status;</br>
+------------------+----------+--------------+------------------+</br>
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |</br>
+------------------+----------+--------------+------------------+</br>
| mysql-bin.000010 \|     1487 \|              \|                  \| </br>
+------------------+----------+--------------+------------------+</br>
1 row in set (0.00 sec)</br>

Slave Recplication Configuration
================================
1) DB 생성 - create database repl_db default character set utf8;
2) 계정 생성 - create user user1@'%' identified by 'password';
3) 권한 부여 - grant all privilages on repl_db.* to user1@'%' identified by 'password';
4) replication 계정 생성 - grant replication slave on *.* to 'repl_user'@'%' identified by 'password';

Slave MySQL Configuration
=========================
vi /etc/my.cnf</br>
[mysqld]</br>
server-id=2</br>
replicate-do-db='repl_db'</br>

Master Server 연결
=================
mysql> change master to</br>
master_host='192.168.65.148',</br>
master_user='repl_user',</br>
master_password='password',</br>
master_log_file='mysql-bin.000010',</br>
master_log_pos=1487;</br>

my.cnf Configuration
====================
[mysqld]</br>
replicate-do-db='repl_db'</br>
master-host='ip'</br>
master-user=repl_user</br>
master-password=password</br>
master-port=3306</br>
server-id=2</br>

Master Server Status 확인
========================
mysql> show processlist\G</br>

*************************** 1. row ***************************</br>
     Id: 1</br>
   User: repl_user</br>
   Host: 192.168.65.149:38488</br>
     db: NULL</br>
Command: Binlog Dump</br>
   Time: 2434</br>
  State: Has sent all binlog to slave; waiting for binlog to be updated</br>
   Info: NULL</br>
*************************** 2. row ***************************</br>
     Id: 2</br>
   User: root</br>
   Host: localhost</br>
     db: NULL</br>
Command: Query</br>
   Time: 0</br>
  State: NULL</br>
   Info: show processlist</br>
2 rows in set (0.00 sec)</br>

Slave Server Status 확인
=======================
mysql> show processlist\G;</br>

*************************** 1. row ***************************</br>
     Id: 1</br>
   User: system user</br>
   Host: </br>
     db: NULL</br>
Command: Connect</br>
   Time: 4294967261</br>
  State: Has read all relay log; waiting for the slave I/O thread to update it</br>
   Info: NULL</br>
*************************** 2. row ***************************</br>
     Id: 2</br>
   User: system user</br>
   Host: </br>
     db: NULL</br>
Command: Connect</br>
   Time: 90</br>
  State: Waiting for master to send event</br>
   Info: NULL</br>
