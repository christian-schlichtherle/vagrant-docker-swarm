# Vagrant Docker Swarm

This project provides a `Vagrantfile` to set up a Docker swarm with one master and two worker nodes.
The number of worker nodes can be set using the environment variable `DOCKER_WORKER_COUNT`.

## Prerequisites

+ [Vagrant](https://www.vagrantup.com)

## Starting A Docker Swarm

To set-up and start a swarm with one master and two worker nodes:

    $ vagrant up 

To change the number of worker nodes to three:

    $ export DOCKER_WORKER_COUNT=3 
    $ vagrant up

## Smoke-Testing The Docker Swarm 

    $ vagrant ssh manager -c "docker node ls"

## Suspending The Docker Swarm

    $ vagrant suspend

## Resuming The Docker Swarm

    $ vagrant resume

## Destroying The Docker Swarm

    $ vagrant destroy

## More Commands

For more commands and options, please refer to the Vagrant [documentation](https://www.vagrantup.com/docs/cli/).
