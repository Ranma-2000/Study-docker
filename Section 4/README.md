# Assignment 2: CLI App Testing
Problem Description:

Imagine yourself being a support engineer for a server farm that runs both Ubuntu and CentOS, and a ticket comes in that asks you to check on the different curl versions in those two distributions.

Step 1: create and run cent:7 image

    docker container run -it -a cent cent:7 bash
    yum update curl
    curl --version

Step 2: create and run ubuntu:14.04 image

    docker container run -it -a ubuntu ubuntu:14.04 bash
    apt update && apt install curl
    curl --version
