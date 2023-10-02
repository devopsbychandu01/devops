docker swarm init
## get the join key after init ##

docker node ls

docker service create --name helloworld alpine ping docker.com
docker service ls
docker ps


docker service create --name hellowrold1 --mode global alpine ping docker.com
docker ps

docker swarm leave --force 