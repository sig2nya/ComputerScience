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
master_host='192.168.65.148',(Master Server IP)</br>
master_user='repl_user',</br>
master_password='password',</br>
master_log_file='mysql-bin.000010',</br>
master_log_pos=1487;</br>

Slave Status 확인
================
mysql> show slave status\G;</br>
*************************** 1. row ***************************</br>
             Slave_IO_State: Waiting for master to send event</br>
                Master_Host: 192.168.65.148</br>
                Master_User: repl_user</br>
                Master_Port: 3306</br>
              Connect_Retry: 60</br>
            Master_Log_File: mysql-bin.000012</br>
        Read_Master_Log_Pos: 434</br>
             Relay_Log_File: slave-relay-bin.000042</br>
              Relay_Log_Pos: 419</br>
      Relay_Master_Log_File: mysql-bin.000012</br>
           <h>Slave_IO_Running: Yes</h></br>
          <h>Slave_SQL_Running: Yes</h></br>
            Replicate_Do_DB: repl_db,repl_db</br>
        Replicate_Ignore_DB: </br>
         Replicate_Do_Table: </br>
     Replicate_Ignore_Table: </br>
    Replicate_Wild_Do_Table: </br>
Replicate_Wild_Ignore_Table: </br>
                 Last_Errno: 0</br>
                 Last_Error: </br>
               Skip_Counter: 0</br>
        Exec_Master_Log_Pos: 434</br>
            Relay_Log_Space: 419</br>
            Until_Condition: None</br>
             Until_Log_File: </br>
              Until_Log_Pos: 0</br>
         Master_SSL_Allowed: No</br>
         Master_SSL_CA_File: </br>
         Master_SSL_CA_Path: </br>
            Master_SSL_Cert: </br>
          Master_SSL_Cipher: </br>
             Master_SSL_Key: </br>
      Seconds_Behind_Master: 0</br>
1 row in set (0.00 sec)</br>

*Slave_IO_Running / Slave_SQL_Running이 정상적으로 YES가 출력되면 Replication 성공
