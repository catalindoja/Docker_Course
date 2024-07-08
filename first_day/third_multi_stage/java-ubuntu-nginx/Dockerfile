# I need to do a multi stage build where one image compiles the java code and the other image runs the java compiled code in a debian
FROM ubuntu AS build
RUN apt-get update && apt-get install -y openjdk-11-jdk
WORKDIR /var/www/html
COPY ./src/SimpleCalculator.java .
# compile the java code
RUN javac SimpleCalculator.java
EXPOSE 80

FROM nginx
COPY --from=build /var/www/html/SimpleCalculator.class /usr/share/nginx/html/SimpleCalculator.class
EXPOSE 80

# start the java code
CMD ["nginx", "-g", "daemon off;"]
