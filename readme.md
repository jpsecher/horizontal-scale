# Horizontal Scale

This is the source code for a horizontally scalable Docker container, who's purpose is to help the initial testing of a container infrastructure like Docker Swarm, Kubernetes, etc.

A running instance will output plain text on HTTP port 80 with a list of all the other instances that it can see on the overlay network, like

       172.17.0.2: 6 visits
    -> 172.17.0.3: 2 visits
       172.17.0.5: 3 visits

The arrow marks the current instance.

## Docker Swarm

Create a stack like

    version: "3.5"
    services:
      counter:
        image: jpsecher/horizontal-scale:latest
        ports:
          - target: 80
            publish: 80
            mode: host
        deploy:
          restart_policy:
            condition: on-failure
          mode: global

which will scale out to every node of the swarm.

## Kubernetes

[TODO: pod def]

----

[![Docker build status](https://img.shields.io/docker/build/jpsecher/horizontal-scale.svg)](https://hub.docker.com/r/jpsecher/horizontal-scale/builds/)
