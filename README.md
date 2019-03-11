# Vagrant Docker Swarm

This project provides a `Vagrantfile` to set up a Docker swarm with a manager and multiple worker nodes.
The number of worker nodes can be set using the environment variable `DOCKER_WORKER_COUNT`.

## Prerequisites

+ [Vagrant](https://www.vagrantup.com)

## Starting A Docker Swarm

To set-up and start a swarm with one manager and two worker nodes:

    $ vagrant up 

To change the number of worker nodes to three:

    $ export DOCKER_WORKER_COUNT=3 
    $ vagrant up

## Smoke-Testing The Docker Swarm 

```bash
$ vagrant ssh manager -c "docker node ls"
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
2805ij9rt6lqd6e8q3mjzzfsd *   manager             Ready               Active              Leader              18.09.3
ntuu4zxr6ja2sk09ay7ge0cy1     worker-1            Ready               Active                                  18.09.3
ajc8la5i93d9rjdjudtsgfl6o     worker-2            Ready               Active                                  18.09.3
Connection to 127.0.0.1 closed.
```

## Suspending The Docker Swarm

    $ vagrant suspend

## Resuming The Docker Swarm

    $ vagrant resume

## Destroying The Docker Swarm

    $ vagrant destroy

## More Commands

For more commands and options, please refer to the Vagrant [documentation](https://www.vagrantup.com/docs/cli/).
