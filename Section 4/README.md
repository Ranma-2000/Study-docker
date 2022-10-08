# Assignment 2: CLI App Testing
Problem Description:

Imagine yourself being a support engineer for a server farm that runs both Ubuntu and CentOS, and a ticket comes in that asks you to check on the different curl versions in those two distributions.

Step 1: create and run cent:7 image

    docker container run -it -a cent cent:7 bash
    yum update curl
    curl --version
    exit
    
Step 2: create and run ubuntu:14.04 image

    docker container run -it -a ubuntu ubuntu:14.04 bash
    apt update && apt install curl
    curl --version
    exit

Step 3: Delete docker images

    docker container rm ubuntu
    docker container rm cent

# Assignment 3: DNS Round Robin Test
https://vegibit.com/dns-round-robin-in-docker/
Problem Description:

DNS Round Robin is the concept that you can have two different hosts with DNS Aliases that respond to the same DNS Name. Where might you find something like this? Consider a service like Instagram. They need more than one server to provide their service, yet users always go to the same Instagram.com domain to use the service. One name, many servers providing the service. In addition to load balancing and server scaling, DNS Round Robin is another technique big companies can use to ensure 24/7/365 uptime. In other words, there are several IP addresses and DNS Records supporting the one public-facing name end-users use(in this case Instagram.com). This same concept applies to containers and in this tutorial we’ll have a look at DNS Round Robin in Docker. 

Step 1: Create a virtual network

    docker network create dns_addr
    
Step 2: Check the network info

    docker network inspect dns_addr
   
Step 3: Create 2 elasticsearch:2 containers

    docker container run -d --network dns_test --network-alias search elasticsearch:2
    
Step 4: Test DNS Round Robin
    
    docker container run --rm --network dns_test centos curl -s search:9200
    docker container run --rm --network dns_test alpine nslookup search
    
    
