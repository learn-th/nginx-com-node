FROM node:latest

WORKDIR /app

RUN apt-get update && apt-get install -y wget

ENV DOCKERIZE_VERSION v0.7.0
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

COPY .docker/node/docker-entrypoint.sh /usr/bin/docker-entrypoint

COPY .docker/node/*.json /app

RUN npm install

EXPOSE 3000

CMD ["docker-entrypoint"]