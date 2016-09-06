### Machines
The demo will run on Digital Ocean droplets. The machine configuration we've chosen for this is
2 GB Memory / 40 GB Disk - Ubuntu 16.04.1 x64. We have the following machines, all in the same region
but different availability zones.
- `manager1` (NYC / AZ1)
- `manager2` (NYC / AZ2)
- `manager3` (NYC / AZ3)
- `agent1`   (NYC / AZ1)
- `agent2`   (NYC / AZ2)
- `agent3`   (NYC / AZ3)

The managers will additionally perform the role of Swarm managers, and agents will only be workers.
So we have 3 managers and 6 workers in total.

### Install Docker
After creating a fresh machine with the above configuration, running the following set of
commands will install Docker on the machine.

```sh
# update the package database
sudo apt-get update

# add the GPG key for the official Docker repository to the system
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

# add the Docker repository to APT sources
echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list

# update the package database once again
sudo apt-get update

# check installation source
apt-cache policy docker-engine

# install Docker Engine
sudo apt-get install -y docker-engine
```

### Set up the Swarm

```sh
# on manager1, start the Swarm (replace the IP address with that of the node)
docker swarm init --advertise-addr 198.211.109.17

# on manager2 and manager3, join the swarm as managers
docker swarm join \
    --token SWMTKN-1-324inlc7148abkfroqreghaxhax6ru6dcf6ru6dcf4y33wgj2t-v3i8vpbvplpbvplv3i8vpbvpl \
    198.211.109.17:2377

# on agent1, agent2, and agent3, join the swarm as workers
docker swarm join \
    --token SWMTKN-1-324inlc7148abkfroqreghaxhax6ru6dcf6ru6dcf4y33wgj2t-6wo8fh6suzkplpluouo3emo7s \
    198.211.109.17:2377

# we must now have a 6 node cluster with 3 manager nodes ready to use
# some basic sanity checks on one or more managers
docker node ls
docker info
```

### Set up a simple nginx service
On the laptop, create an nginx image from the code present in the `demo` directory. To build and push
the image, run

```sh
docker build -t username/london:tag .

# remember to login using docker login before pushing
docker push username/london:tag
```
On `manager1`, run the following command.

```sh
docker service create --name nginxdemo --publish 80:80 --replicas 2 username/london:tag`
```