Intro
--------------------------------------------

This is basically a TLDR for the ELK stack. Basically a way to copy and and paste to get the ELK environment up and running using docker containers.
It will spin everything up and generate some fake data (40,000 entries).
It's also setup to run an elasticsearch cluster.  By default it will run a master and a slave node, see below if you want to scale to more nodes.

**WARNING: THIS WILL HAMMER ON YOUR SYSTEM RESOURCES AS IT GENERATES A TON OF DATA QUICKLY.**


Prerequisites
--------------------------------------------
You need to have docker and docker compose installed to be able to run this setup.


To install docker follow the guide at: https://docs.docker.com/installation/

Last tested working with:
 
 - Docker (v.1.11.2)
 - Docker Compose (v.1.7.0)

Running
--------------------------------------------
Very simple, just enter in the directory and run the single command below.

    canned-elk-dir/> docker-compose up -d

That will take a few seconds and is setup to generate 40,000 random data entries into the ELK stack.  This will be taxing on your system, but once it's done generating data the system should settle back down.


Then Follow these steps:
  1. Open your browser and go to http://localhost:5601.  You should see Kibana start up.
  2. You will need to select an index to use.  Click the input form box and a drop down should open with the option "@timestamp", select this then click save. 
  3. From there you should see indexs have been mapped out.
  4. Click the discover button to start exploring your generated data


Scaling the cluster
--------------------------------------------
It is very easy to scale up the cluster and to verify it has been scaled up.
From your host system you can run curl to check the status.

    > curl localhost:9200/_cat/nodes
    172.24.0.2 172.24.0.2 8 87 0.50 d * Honcho       
    172.24.0.3 172.24.0.3 7 87 0.50 d m Richard Fisk 


Now let's make the cluster have 5 nodes (master + 4 slaves):

    canned-elk-dir/> docker-compose scale es_slave=4

Then if wait a little bit (~30-60 seconds) the nodes should have started and auto-joined the cluster.  To verify you can run curl again to confirm.

    > curl localhost:9200/_cat/nodes
    172.24.0.6 172.24.0.6 7 95 0.74 d m Mephisto       
    172.24.0.2 172.24.0.2 3 95 0.74 d * Honcho         
    172.24.0.8 172.24.0.8 7 95 0.74 d m Melody Guthrie 
    172.24.0.3 172.24.0.3 7 95 0.74 d m Richard Fisk   
    172.24.0.7 172.24.0.7 7 95 0.74 d m Shathra   
  
There you can see the 5 nodes in the cluster.



Shutting down
--------------------------------------------
It's very easy to remove the old data and clean up the environment

    > docker-compose down

