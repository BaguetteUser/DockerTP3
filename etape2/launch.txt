docker run -d --name data --network monreseau -e MARIADB_ROOT_PASSWORD=password -v "$(pwd)/bdd:/docker-entrypoint-initdb.d" mariadb

docker build -t php-mysqli ./confPHP

docker run -d --name script --network monreseau -v "$(pwd)/monsite:/app" php-mysqli

docker run -d --name http --network monreseau -p 8080:80 -v "$(pwd)/config/default.conf:/etc/nginx/conf.d/default.conf" -v "$(pwd)/monsite:/var/www/html" nginx

