# Elastic_Condor_AWS
Elastic Condor pool implemented using HTCondor 8.2.4 running on Amazon Web Service’s EC2. Partner: Christopher Croson

Elastic Condor Pool: a system that monitors a Condor pool and allocates machines from Amazon Web Services 
EC2 as needed. The implementation of the system would take into account aspects such as performance, 
cost efficiency, and responsiveness.

●	HTCondor 8.2.4 & Amazon Elastic Compute Cloud

Manage_pool script:  For the pool manager, we designed a Cron job that was scheduled to automatically 
run our pool management script every 5 minutes. This script evaluates the current state of the worker pool and 
job queue and adjusts the pool size as needed. Thus, the pool can respond to changes in work conditions within 5 minutes. 
In the script itself, the minimum and maximum number of machines that can be present in the pool are set and, 
for our testing purposes, we decided on 2 for the minimum, as it provided us with a cost efficient set up which 
did not have to rely on a single machine and 10 for the limit, again, with cost being a priority, as well as keeping 
the nature of our jobs in mind. Of course, the limit can be set differently, where a user can prioritize cost over 
run time or viceversa.  The script then retrieves information from the Condor pool, including the total number of machines 
present, as well the number of idle machines and active machines, and stores them as variables. 
Data from the queue, which is relevant to the jobs, is also saved.  

The queue data is composed of the status of the job, which is extracted using grep. 
Job info, idle jobs, and the number of tasks are also stored in this section. 

