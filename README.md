# ContainerCamp2016
This repo contains code and relevant material for my ContainerCamp UK 2016 talk (Sept. 9, 2016) in London.

## Abstract
Although containers are bringing refreshing flexibility when deploying services in production, the
management of those containers in such an environment still requires special care in order to keep
the application up and running. On this front, orchestration platforms like Docker, Kubernetes and
Nomad have been trying to alleviate this responsibility, facilitating the task of deploying and
maintaining the entire application stack in its desired state. This ensures that a service will
always be running, tolerating machine failures, erratic network behavior, or software updates and
downtime.

The purpose of this talk is to explain the mechanisms used in the core Docker Engine orchestration
platform (using a framework called SwarmKit) to tolerate failures of services and machines, from
cluster state replication and leader-election to container re-scheduling logic when a host goes down.
