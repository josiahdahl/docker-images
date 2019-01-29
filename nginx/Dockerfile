FROM nginx:alpine

LABEL maintainer="Josiah Dahl <josiah.dahl@gmail.com>"

COPY nginx.conf /etc/nginx

RUN apk update --no-cache \
    && apk upgrade --no-cache \
    && adduser -D -H -u 1000 -s /bin/sh www-data

CMD ["nginx"]

expose 80
