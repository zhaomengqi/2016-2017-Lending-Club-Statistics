
# Web-Spider-for-grabing-IBM-Database


## Problem 1: Data wrangling Edgar data from text files 
### Part 1: Parse files https://datahub.io/dataset/edgar 
The goal of this exercise is to extract tables from 10Q filings using Python Given a company with CIK (company ID) XXX (omitting leading zeroes) and document accession number YYY (acc-no on search results), programmatically generate the url to get data (http://www.sec.gov/Archives/edgar/data/51143/000005114313000007/0000051143-13-000007- index.html for IBM for example). 

Parse the file to locate the link to the 10q file (https://www.sec.gov/Archives/edgar/data/51143/000005114313000007/ibm13q3_10q.htm for the above example). 

Parse this file to extract “all” tables in this filing and save them as csv files.

### Part 2: Dockerize this pipeline
Build a docker image that can automate this task for any CIK and document accession number which could be parameterized in a config file. We should be able to replace IBM’s CIK and document accession number with Google's to generate the url https://www.sec.gov/Archives/edgar/data/1288776/000128877615000046/0001288776-15-000046- index.htm and then parse this document to look for the 10Q filing https://www.sec.gov/Archives/edgar/data/1288776/000128877615000046/goog10-qq32015.htm and extract all tables from this filing. 

The program should log all activities, then zip the tables and upload the log file and the zip file to Amazon S3. 

Parameterize your cik, accession number and amazon keys so that anyone can put their cik, accession number and amazon keys and locations and reuse your code. 

              
## Problem 2: Missing Data Analysis 
Analyze the EDGAR Log File Data Set [https://www.sec.gov/data/edgar-log-file- data-set.html ]. The page lists the meta data for the datasets and you are expected to develop a pipeline which does the following. 

The program (In Python) should get data for the first day of the month(programmatically generate the url http://www.sec.gov/dera/data/Public- EDGAR-log-file-data/2003/Qtr1/log20030101.zip for Jan 2003 for example ) for every month in the year and process the file for the following:

• Handle missing data

• Compute summary metrics (Decide which ones)

• Check for any observable anomalies

• Log all the operations (with time stamps) into a log file

• Compile all the data and summaries of the 12 files into one file

• Upload this compiled data file and the log file generated to Amazon S3 bucket on Python packages to use for this.

• Create a Docker image which runs the pipeline. 

• Try Docker image on AWS and run it for 2005 and share the locations for the AWS bucket with the processed data and log file in the report

