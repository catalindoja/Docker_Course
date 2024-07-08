# install php in ubuntu, then use multi stage building to get the files in ngnix and show the php info from the index.php file
FROM ubuntu AS build
RUN apt-get update && apt-get install -y php
WORKDIR /var/www/html
COPY index.php .
EXPOSE 80

FROM nginx
COPY --from=build /var/www/html/index.php /usr/share/nginx/html/index.php
EXPOSE 80

# start the index.php
CMD ["nginx", "-g", "daemon off;"]
