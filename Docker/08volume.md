Docker volume ls
## named volumes
docker volume create <volumeName>
docker volume inspect <VolumeName>
## named volumes
docker run -d --name devtest -v myvol2:/app nginx:latest
docker run -d --name=nginxtest -v nginx-vol:/usr/share/nginx/html nginx:latest
## host volumes
docker run -d --name=nginxtests --mount source=nginx-vol,destination=/usr/share/nginx/html nginx:latest
## create annonimous volumes
docker run -d --name=nginxtest -v /usr/share/nginx/html nginx:latest
