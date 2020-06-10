# PostgreSQL Notes and Cheet Sheet Commands.
## Server/Container Setup
### Volumes
* Setup seperate volumes for each 
  * database data
  * pg_xlog - this handles all WAL files for transactions and replication
  * backup area and dumps of database

