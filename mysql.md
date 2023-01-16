#MySQL Commands

## Replication issues
### Too many BIN logs files
Create space on the drive.
Connect to the database and run the following to clean out old bin logs with the following.
```
PURGE BINARY LOGS TO 'log_name';
PURGE BINARY LOGS BEFORE '2022-11-06 00:00:00';
```
