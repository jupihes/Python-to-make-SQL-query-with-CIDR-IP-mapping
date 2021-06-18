# Python-to-make-SQL-query-with-CIDR-IP-mapping
Python to make SQL query with CIDR IP mapping

Using Python to ease making and running SQL queries

Please read this manual to use python scripts to make and execute SQL queries for some specific purposes easier.
Purpose
Running a desired SQL query for a list of IPs for some days.
 
Steps
STEP0: install required packages
•	Type this into Spyder IPython Console:
o	!pip install netaddr
STEP1: Make the SQL file contain your IP list 
•	Copy the list of your desired IP list (with or without subnet mask. Ex: /24) to “IP_Net_pool.xlsx”
•	Copy your desired SQL template into the folder
o	Instead of unix day suffix insert [?D?]
o	Instead of the IP list insert [?IP?]
o	Ex:






•	Modify Subnet_Regex_IP_SQL v1.0.py to have your SQL template file name
•	Run Subnet_Regex_IP_SQL v1.0.py
o	Doing this will generate two “csv” file. 
o	Note: This python script will remove duplicated addresses, sort, and summarize the IP list
•	Now a SQL file generated that contains the provided list of IPs instead of [?IP?]

STEP2: Run SQL using python on the server
•	Copy generated SQL file to the server on below address on server:
o	D:\...\carbon
•	Modify multiple_days_query.py to have your SQL file name and range of intended days
o	Ex: In the below script the query will be executed for last 10 days.





•	Execute multiple_days_query.py using spyder 
•	The fetched data will be shown up on “output” folder. One csv file for each day.
Notes:
1.	It is better to first run the query for one day and check its output, when you ensure that it works correctly run it for longer periods.
2.	You can check the elapsed time for executing and fetching query in the console.
3.	If spyder showed a connection error, close spyder and open it again

