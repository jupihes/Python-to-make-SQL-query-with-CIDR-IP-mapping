# Python-to-make-SQL-query-with-CIDR-IP-mapping

Authors: 
Hossein Khayami @https://github.com/h-khayami main contributer <br>
Hesam Mohammad Hosseini@https://github.com/jupihes supported to revise and add all sections to make one unified program <br>

## Background


"CIDR Notation to Regex Tool" http://d.xenowire.net/cidr2regex.php used and few bugs on ??? modified.


# Python to make SQL query with CIDR IP mapping

Using Python to ease making and running SQL queries

Please read this manual to use python scripts to make and execute SQL queries for some specific purposes easier.
## Purpose
Running a desired SQL query for a list of IPs for some days.

![Schematic](https://github.com/jupihes/Python-to-make-SQL-query-with-CIDR-IP-mapping/blob/main/schematic%20of%20workflow.jpg)

## Steps

### STEP 0:  install required packages

- Type this into Spyder IPython Console:
  - !pip install netaddr

### **STEP 1:** Make the SQL file contain your IP list 

- Copy the list of your desired IP list (with or without subnet mask. Ex: /24) to *“IP_Net_pool.xlsx”*

- Copy your desired SQL template into the folder

  - Instead of unix day suffix insert [?D?]

  - Instead of the IP list insert [?IP?]

    Example

```sql
SELECT server_ip, sum(L4_UL_THROUGHPUT)
from ps.detail_ufdr_fileaccess_[?D?] 
where server_ip in ([?IP?])
group by server_ip
```

 

- Modify *Subnet_Regex_IP_SQL v1.0.py* to have your SQL template file name
- Run *Subnet_Regex_IP_SQL v1.0.py*
  - Doing this will generate two “csv” file. 
  - Note: This python script will remove duplicated addresses, sort, and summarize the IP list

- Now a SQL file generated that contains the provided list of IPs instead of [?IP?]

 

### **STEP 2:** Run SQL using python on the server

- Copy generated SQL file to the server on below address on server:

D:\\...\carbon

- Modify *multiple_days_query.py* to have your SQL file name and range of intended days
  - Example: In the below script the query will be executed for last 10 days.

```python
for i in range (1,11):     
    x.query_to_csv(sql_file, query_path,save_path, day_diff=i)
```

- Execute *multiple_days_query.py* using spyder 
- The fetched data will be shown up on “output” folder. One csv file for each day.

Notes:

1. It is better to first run the query for one day and check its output, when you ensure that it works correctly run it for longer periods.

2. You can check the elapsed time for executing and fetching query in the console.

3. If spyder showed a connection error, close spyder and open it again

 
