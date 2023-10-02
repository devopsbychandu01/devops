docker swarm init
## get the join key after init ##

docker swarm join --token SWMTKN-1-3sbv1kso2s5luypmipre34c477yntep33tgxpvgyoo9tpr9rxd-c556m3y6u5f34hg0ha18dysr1 10.0.0.4:2377

docker node ls

docker service create --name helloworld alpine ping docker.com
docker service ls
docker ps


docker service create --name hellowrold1 --mode global alpine ping docker.com
docker ps

docker swarm leave --force 