# smppserver
Linux based smppserver - project. SMPPsever can receives sms on SMPP protocol. High TPS of 3000 sms per second.

🛠️ Requirements & System Environment

• Operating System: Linux (Ubuntu/CentOS/RHEL)
• Language: C (compiled binary)
• Database: MySQL / MariaDB

Below is the structured breakdown of the configuration settings. Ensure all database fields and tables exist before starting the server application.

1. Core SMPP Server Settings [smppserver]

This section controls the network bindings, thread pooling, session counts, and basic logging paths for the application.
• smpp-api-key: Security token assigned to the SMPP API interface.
• smpp-host: The network IP address the SMPP service binds to.
• txport / rxport: The mandatory binding ports for Transmitter (TX) and Receiver (RX) connections.
• http-host / http-port: Host IP and port dedicated to the HTTP administration interface.
• http-pass: Administrative password required to access HTTP endpoints.
• smpp-worker-thread: Number of concurrent worker threads. Dependent on CPU multi-core availability and expected ESME connections.
• smpp-version: The designated SMPP version protocol rule (e.g., internal value 52).
• max-sessions: Maximum number of concurrent ESME client connections allowed (Max: 499).
• dlrsmlimit / dlrsleep: Configuration for Delivery Receipt throttling limits and sleep cycle timings (in microseconds).
• log-file / access-log / http-log: Absolute Linux directory paths for system, connection, and HTTP traffic logs.


2. Master Database Connection [mysql-db-master]

Handles client profiles, authentication rules, status validation, and financial credit limits.
• Authentication Flag Levels (flag-check-bind):
	• 0: Validates only username, password, and smppid.
	• 1: Validates credentials + structural bindtype (TRX/TXRX).
	• 2: Strict validation. Validates credentials + bindtype + active status + profile expiration validity date.
• Credit Flag (flag-check-credit): If enabled (1), checks balance counts per SMS request. Note: Enforcing this at the SMPP layer may lower maximum TPS performance.


3. Buffer Database Allocation [mysql-db-buffer]

Manages incoming queues and parts processing before transmission.
• buffer-longsms: Table target used automatically to segment or queue concatenated long SMS parts.
• buffer-smppbuffer: List of active standard queues. The server accepts up to 50 comma-separated database tables to distribute message loads.
• buffer-raw-sms:
	• 1: Raw incoming capture. Skips structural data conversion or character set concatenation, dumping loads directly into a single active buffer.
	• 0: Decodes GSM configurations into ISO-8859, standardizes UTF-16 arrays into standard UTF-8 text formats, runs automated concatenation strings, and round-robins across distinct table arrays.


4. Delivery Receipts Engine [mysql-db-dlr]

Dedicated persistence loop layer for managing processing updates, asynchronous state logs, and vendor receipts back to the client application.

contact : dhrubajhaldar@gmail.com
