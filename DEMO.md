### Machines
The demo will run on Digital Ocean droplets. The machine configuration we've chosen for this is
2 GB Memory / 40 GB Disk / SFO2 - Ubuntu 16.04.1 x64. We have the following machines
- `manager-sfo1` (SF region)
- `manager-nyc1` (NYC region)
- `manager-tor1` (Toronto region)
- `agent-sfo1` (SF region)
- `agent-nyc1` (NYC region)
- `agent-tor1` (Toronto region)

The managers will additionally perform the role of Swarm managers, and agents will only be workers. So we have 3 managers and 6 workers in total.

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

### Setup the Swarm