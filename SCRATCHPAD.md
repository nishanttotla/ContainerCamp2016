This file represents the set of useful presentation ideas.

A first set of useful points
- service replication
- desired state reconciliation
- cluster state replication
- raft
- mesh networking
- gossip protocol

A second (more elaborate) set of useful points
- start by talking about how replication is the most fundamental way you can start with high availability
- and then go into how you can use desired state reconciliation to maintain your replication
- and then talk about how you replicate cluster state so that your desired state engine is also HA
- and then explain how raft ensures that your replicated cluster is consistent
- and then switch gears and talk a bit about networking.

### Fundamentals and Learnings

- Regions vs Availability Zones: Regions are easy to understand. They are completely isolated from
each other and are in different parts of the world. Although unusual, failures do happen. AWS
therefore provides availability zones that are isolated from each other (they have low latency
connections). Deploying your application across multiple availability zones makes you ready for
unexpected outages. So if there is an outage with a particular availability zone your application
stays online.

### Useful Links
1. [How to create your first Digital Ocean Droplet](https://www.digitalocean.com/community/tutorials/how-to-create-your-first-digitalocean-droplet-virtual-server)
2. [How To Install and Use Docker on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)