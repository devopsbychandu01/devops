## get the join key after init ##
docker swarm init

### Join the manager
docker swarm join-token manager

### worker join
docker swarm join --token SWMTKN-1-2uyyxl7anaqjc5gjqxrhc2vruuw1t6rmmfbcjnnxvpitbhd2ar-b7xmgk9j1224drceen3ztlhwd 10.0.0.4:2377

docker node ls
docker swarm leave --force 

<!-- docker service create --name helloworld alpine ping docker.com
docker service ls
docker ps


docker service create --name hellowrold1 --mode global alpine ping docker.com
docker ps -->

docker-compose up -d
docker-compose down





docker stack deploy -c docker-compose.yml mydeployment

## https://forums.docker.com/t/docker-swarm-deploy-container-only-to-worker-nodes-service-only-reachable-from-manager/78147/6