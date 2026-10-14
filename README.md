# smppserver
Linux based smppserver - project. SMPPsever can receives sms on SMPP protocol. High TPS of 3000 sms per second.
[smppserver]
smpp-api-key = "your_secret_api_key_here"
smpp-host = "x.x.x.x"
txport = 9911
rxport = 9912
http-host = "x.x.x.x"
http-port = 9191
http-pass = "your_secure_http_password"
smppid = "SMPP9911"
system-type = "DJHSM"
smpp-worker-thread = 8
smpp-version = 52
bind-ton = 0
bind-npi = 0
log-file = "/var/log/smppserver/server.log"
access-log = "/var/log/smppserver/access.log"
http-log = "/var/log/smppserver/http.log"
http-display-level = 0
max-sessions = 499
dlrsmlimit = 1000
dlrsleep = 500000
dlr-resend = 3600
mysql-keepalive = 3600

[mysql-db-master]
master-dbhost = "x.x.x.x"
master-dbname = "mock_master_db"
master-dbuser = "mock_user"
master-dbpass = "mock_password"
master-dbport = 3306
master-poolsize = 5
smpp-users-tablename = "smpp_users"
smpp-users-field-smppid = "smppid"
smpp-users-field-username = "username"
smpp-users-field-password = "smpp_pass"
smpp-users-field-userid = "userid"
smpp-users-field-parentid = "parentid"
smpp-users-field-bindtype = "bindtype"
smpp-users-field-usertype = "pushtype"
smpp-users-field-credittype = "credittype"
smpp-users-field-status = "status"
smpp-users-field-credit = "credit"
smpp-users-field-mincredit = "min_credit"
smpp-users-field-expirydate = "accvalidity"
smpp-users-field-clientip = "client_ip"
flag-check-credit = 1
flag-check-bind = 0
flag-check-ipaddress = 1

[mysql-db-buffer]
buffer-dbhost = "x.x.x.x"
buffer-dbname = "mock_buffer_db"
buffer-dbuser = "mock_user"
buffer-dbpass = "mock_password"
buffer-dbport = 3306
buffer-longsms = "smpp_buffer_long"
buffer-smppbuffer = "smpp_buffer001,smpp_buffer002,smpp_buffer003"
buffer-poolsize = 5
buffer-raw-sms = 1

[mysql-db-dlr]
dlr-dbhost = "x.x.x.x"
dlr-dbname = "mock_dlr_db"
dlr-dbuser = "mock_user"
dlr-dbpass = "mock_password"
dlr-dbport = 3306
dlr-smppdlr = "smpp_dlr_records"
dlr-poolsize = 1
