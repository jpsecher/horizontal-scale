# Horizontal Scale

This is the source code for a horizontally scalable Docker container, who's purpose is to help the initial testing of a container infrastructure like Docker Swarm, Kubernetes, etc.

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
