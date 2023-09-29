Docker volume ls
Docker volume create <volumeName>
Docker volume inspect <VolumeName>
docker run -d --name devtest -v myvol2:/app nginx:latest
docker run -d --name=nginxtest -v nginx-vol:/usr/share/nginx/html nginx:latest
Docker run –d --name=demo -v /opt/demo:/usr/share/nginx/html nginx:latest
docker run -d --name=nginxtest -v /usr/share/nginx/html nginx:latest
