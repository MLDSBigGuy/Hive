# Hive

Hive is a datawarehoiuse built on top of hadoop. It is a dictributed system. Oline alnyltical processing can be done with hive

- Transactional processing (Traditional RDMS)
  Analyzes individual entries, recent data, updates data, fast real time access , single data source

- Analytical processing (Distributed coputing framewrok..needs datawarehouse)
  Analyzes Large batches, older, reads data, long running jobs, multiple data sources
  
- Small data - single machine , weel.dfeined structured data, no replication, can access individual records for entire dataset, 

- Big data - very hard to meer all req. with same db system
  Data distributed on cluster 
  semi or unstructured 
  No random access to data 
  dta repicated acfross multipe machines (replicas also updated) 
  diff. sources may have diff unknown formats 
  
- Hbase is db runs on top of hadoop for transcational processing , qlikview for single machine for analytical processing 

- www.informatica.com def of data warehouse
  - tech that aggregates data from one or more source s so thAt it can be compared and analyzed for greater BI
  - DW have long running batch jobs, read operations, from muliple sources, hols data over long perio fo ftime , NOT EAL TIME
  - DW examples -  vertica, teradata, oracle, ibm (company owns these softwares and not opensource
)

- APACHE Hive is open source DW is part of karger hadoop ecpsystem 

- Hadoop can store millions of records, fault tolerant and recoversy when nodes crash
  - HDFS - data storage for hadoop

  - Mapreduce is parallel procesing framework to process data across mltiple machines

  - YARN - cordinator that says where processes can run
  
   
- Hive queris are transalted to mapreduce jobs. Mapreduce defines the actual logic. MR are batch processing applications , jobs run fro days, mapreduce code in java. Hive harness the power of mapreduce without writing any java code

- HiveQL similar to  sql, analyst and enginners are familar with these simple query construclrs like select, group by,m join. Each of thes e stmst are converted to hive

- Hive sees data in form of tables although hdfs store it in files (hive metastore takes care of this conversion of file to tables exposed to user) 

- Hive DW and RDBMS
  - Data size (Hive for big data, rdms for small data
  - Computatuon (parallel computations....distributrd sys with multiple machines, serial...single pc with backup one mastern one slave 
  - Latency (High, Low
  - Operations (read...bczo its not he owner of data...can be use by hadoop, pig, sprak ; read&write ...sole gatekeeer for data....primary key, foriegh kess possible becoz ofthis 
  - ACID (Not acid complaint...data can be dumped into hive from any source; acid...only data which satisfies constrints can be dumped
  - Query lang (HiveQL; SQL
  - Datasets ( GB/TB, MB/GB
  - Trends,Access&updates records
  - semi structured, structured and adheres to table schema
  - disk space cheap as u can add machines upon need, disk space costly
  - records no indexed and cannot be accesd quickly, records can be indexed to look up info or update info fast
  - fetching a row run mapreduce taked even minutes, queries answered in ms
  - Schema on read ; schema-on-write (all columns matche and row match hen only table schema is matchedd
  
  
- HiveQL and SQL
  - minimal index, index allowed
  - many built-in function as it is analytical db, basic built-in
  - only equi-joins, subqueries; any subqueries 
  
- Beeline CLI is hive command line interface for hivesewrver2
- Hive CLI 

- similarities with hive and sql
  - show databses; 
  - create database dbname;
  - use dbmane; (to use tis db
  - create table customers (id bigint, name string);
  - show customers;
  - describe customers (all columns that table has will be displayed
  - insert into customers values ((111, "john2"), (222, "fsfs#"));
  - select * from customers where address =""; and/or id<222
  - select DISTINCT from customers 
  - select name from custimers order by/group by address;
  - create table if not exists orders (amoubt double, d biginit);
  - describe orders
  - show databases like 'pl*'  
  - drop table test;
  - builtin user defined functions functions - count(*), avg, sub....
  - nano read_custo,ers.sql (contains all series of commands to run in hive) just likex.sql file
  - joins in hive are complex.Hive only supports equi joins (where customer.cust_id = order.cust_id) only = no < or >
  
- Hive data types (primitive and complex)
  - 4 primitive (boolean (t/f), numeric (int /decimal), string, timestamp
    - INT - tinyint (1 byte -128 to 128,), small int (2 bytes), int (4 bytes), bigint(8bytes)
    - DECIMAL - Float (4 bytres), double (8 ), decimal )dec(10,2)--decima precision oof  digits 
    - String - string (unbouned lgth, variable), char- fixed lgth string , varchar (bounded., has an upper limit), varchar is optimal than char in terms of storage 
    - TIMESTAMP - Integers (unix timestamp in ns)., Flaots (unix timestamp in seconds with decimal precison), String ( jdbc complaint - "yyy-mm-dd-hh-ss-ms)", Dates ("yyyy-mm-dd")
   
-  Hive Tables (Data is stored in hdfs , files across multiple machines, 
  - Managed (managed by hive and stored in dw , External (not fully managed by hive and stored out of dw)
  - managed table deletion deleted data and metadat. extrenal in use by othe pig, hbase doesnot delte data. deleteds only metadat 
  - products.csv sepearted by commas to be imported to hive 
  - create external table if not exists products ()
  - row format delimited fields terminated by ',' - telling hive how data is formated in haddop data fokder 
  - stored as textfile (say hive what kind of file it is ) 
    - go to all other file types in apache create table ddl wiki reference)
  - location '/data/' (data folder in hdfs 
  - comment "table extra infoe"
  - alter table fresh_products rename to freshproducts
  - alter table x add colu,ns (exi ..
  - alter table x change column id id string after title; 
  
- Temporary tabels for temp data (all ur team can have same temp table name and they donot szpport partitins or index. can have same name as permanent table. if u hjvae tmpo tabel. the u ccnt accces permannte one=)
  - create temporatay table customer lie customers
- load data local inpath "x.cav' into table x;
- seelct * from x; -shows all details in csv gettig transalted to hive table. Empty lines also loadesd as null. 
  
- Load multiple tables 


- Partitioning and Bucketing for query performace optimizations (Huge concept not covered here completeyl) 

  
- complex data types
  - Array
    - Ex: colors array<int>
  - Map
    - no fixed size and unordered collection of  key value pairs, 
         Ex: features map<string, boolean>
          map keys terminated by ':';
        - amp enables s to look up values using key (like json')
  - Struct
    -logical grouuping, can have different data types within 
    Ex: information struct <battery:string, camera:string>
        collection iterms terminated by # 
 
- Built-in fnctions (udf , udaf (z´sed defined af´ggrefggate , udtf 8table generating funcitons)) 
  - udf works on single row and outputs single row
    - trim(), concat(), lenght(), round(), floor()
  - udaf works on multipe rows and outputs single row
    - counbt(*) , sum, avg()
  - udtf works on single row and output multiple rows 
    - explode() - flatten the data in arrays or maps , posexplode() ...same as explode´() with index or postion of originla item
    - Ex: select explode(colors) as variants from mobilephones {array}
          select explode (features) as (feature, present) {map }
  
- lateral keword enables you o create a virtual table which u can miy later with original table 
  - Ex:lateral view explode(colors) colorTable as variant; colorTable is thevirtual table. This virtual table is automatically joined with original table mobilephones 
  
- Design schema for rdbms
  - normalized storage in traditional db ( data stored in granular form to minimize redundancy, optimize storage for single machine holding all the data, foreign keys to ensure valid joins, updates and write to tables is easy as thery all reside in one locations and no duplication of data) 
    - employee info splited in many tables like name, id, address, subordinate, like manager specifi info, person specifi info etc,., to minimize the redundancy while stroing. U split data tinto logical groups 
  - hive used denormalized storage (scheam desing for hive depends on dataset and kind of quereis to run on them) 
 -  Design schema for hive   
    - col structure and data types, seerialzed forms in hdfs , partition by columns to improve query performace , speed of sampli ng and join opearations depends on how u bucket
    - data compressed to one table be read in single opeatration. All data is in single table 
    - disk sapce is cheap in big data system. easy to add machines and increase storage
    - no foreign key constrainmts
    - join are heavy duty opeartions in hive ( elimiate them as much as possible) 
    - read opreations, no updates
    - mimnimize the number of disk seeks. In big data, time takes to see where data resides
    - Ignore redundany, minimize joins
    - get all details about an emlloyee in one read opearation
    
    
    

    




  
  

  
