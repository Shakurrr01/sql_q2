Microsoft Windows [Version 10.0.22631.4169]
(c) Microsoft Corporation. All rights reserved.

C:\Users\Abdulshakur>cd ..

C:\Users>cd ..

C:\>sqlplus / as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Thu Oct 3 20:42:58 2024
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> show pdbs;

    CON_ID CON_NAME                       OPEN MODE  RESTRICTED
---------- ------------------------------ ---------- ----------
         2 PDB$SEED                       READ ONLY  NO
         3 XEPDB1                         READ WRITE NO
         4 PLSQL_CLASSNAME2024DB          MOUNTED
SQL> CREATE PLUGGABLE DATABASE mu_to_delete_pdb
  2  ADMIN USER mu_plsqlauca IDENTIFIED BY 123
  3  FILE_NAME_CONVERT = ('C:\app\Abdulshakur\product\21c\oradata\XE\','C:\app\Abdulshakur\product\21c\oradata\XE\mu_to_delete_pdb');

Pluggable database created.

SQL> show pdbs;

    CON_ID CON_NAME                       OPEN MODE  RESTRICTED
---------- ------------------------------ ---------- ----------
         2 PDB$SEED                       READ ONLY  NO
         3 XEPDB1                         READ WRITE NO
         4 PLSQL_CLASSNAME2024DB          MOUNTED
         5 MU_TO_DELETE_PDB               MOUNTED
SQL> drop pluggable database mu_to_delete_pdb;
drop pluggable database mu_to_delete_pdb
*
ERROR at line 1:
ORA-65179: cannot keep datafiles for a pluggable database that is not unplugged


SQL> drop pluggable database mu_to_delete_pdb including datafiles;

Pluggable database dropped.

SQL> show pdbs;

    CON_ID CON_NAME                       OPEN MODE  RESTRICTED
---------- ------------------------------ ---------- ----------
         2 PDB$SEED                       READ ONLY  NO
         3 XEPDB1                         READ WRITE NO
         4 PLSQL_CLASSNAME2024DB          MOUNTED
SQL>
