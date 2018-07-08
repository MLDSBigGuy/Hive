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

- 
  
  

  
