docker network create monreseau

docker container run -d --name script --network monreseau -v "$(pwd)/app:/app" php:fpm

#j'ai modifié le fichier config.conf sur mon pc.
docker container run -d --name http --network monreseau -p 8080:80 -v "$(pwd)/app/index.php:/app/index.php" -v "$(pwd)/default.conf:/etc/nginx/conf.d/default.conf" nginx


