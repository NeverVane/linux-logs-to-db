# linux-logs-to-db
A Bash script to efficiently import Linux log files from /var/log and its subdirectories into a MySQL database table. It handles de-duplication and batch processing to optimize performance.


## Usage Guide:

### Clone the repository

```
git clone https://github.com/yourusername/linux-log-to-db.git
cd linux-log-to-db
```

### Import the database schema into the db server:

```
mysql -u your_mysql_user -p your_mysql_password your_database_name < logs_schema.sql
```

### Configure the script:
```
DB_USER=your_mysql_user
DB_PASSWORD=your_mysql_password
DB_NAME=your_database_name
SSH_USER=your_ssh_user
SSH_HOST=your_ssh_host
SSH_PORT=your_ssh_port
SSH_PASSWORD=your_ssh_password
```

### Run the script:
```
chmod +x log_to_db.sh
./log_to_db.sh
```

### Schedule the script:
```
*/2 0 * * * /path/to/linux-log-to-db/log_to_db.sh
```




The script is written to run command on the remote machine ( in my case the db server is a remote host ) using sshpass ( in order to use password as authentication method over key auth - you can change that easily ), because I didn't want to allow remote db connections.
This way the db server could be an aggregator for logs of different Linux hosts.
