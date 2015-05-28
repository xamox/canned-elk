This is basically a TLDR for the ELK stack.  This is basically a way to copy and and paste to get the ELK environment up and running using docker containers.


## Prerequisites
You need to have docker and docker compose installed to be able to run this setup.

To install docker follow the guide at: https://docs.docker.com/installation/

Or if you are on a debian based distribution:

	sudo apt-get update
	sudo apt-get install wget
	wget -qO- https://get.docker.com/ | sudo sh
	sudo curl -L https://github.com/docker/compose/releases/download/1.2.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
	sudo chmod +x /usr/local/bin/docker-compose


## Running
Very simple, just enter in the directory and run the single command below, then open your browser and go to http://localhost:5601.  You should see Kibana start up.  You will need to select an index to use.  Click the input form box and a drop down should open with the option "@timestamp", select this then click save.  From there you should see info flowing into kibana.  This setup uses the generator plugin for logstash to generate fake data for the system.