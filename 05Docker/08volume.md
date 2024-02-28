Docker volume ls
## named volumes
docker volume create <volumeName>
docker volume inspect <VolumeName>
## named volumes
docker run -d --name demo1 -v myvol1:/app nginx:latest
docker run -d --name=demo2 -v nginx-vol:/usr/share/nginx/html nginx:latest
docker run -d --name=demo2 -v testing:/usr/share/nginx/html nginx:latest
## host volumes
docker run -d --name=hostvolumeContainer -v /opt:/usr/share/nginx/html nginx:latest
## create annonimous volumes
docker run -d --name=nginxtest -v /usr/share/nginx/html nginx:latest
