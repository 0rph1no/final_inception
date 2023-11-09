From debian:buster

RUN apt-get update -y
RUN apt-get install nginx openssl -y
RUN apt-get upgrade -y
COPY ./default /etc/nginx/sites-available
COPY ./content/index.html /var/www/html
COPY ./initializer.sh /usr/local/bin
RUN chmod 777 /usr/local/bin/initializer.sh
# RUN /usr/local/bin/initializer.sh
RUN mkdir -p /etc/encryption
RUN openssl req -x509 -nodes -days 365 -subj "/C=CA/ST=QC/O=Company, Inc./CN=ceddibao.42.fr" -addext "subjectAltName=DNS:ceddibao.42.fr" -newkey rsa:2048 -keyout /etc/encryption/localhost.key -out /etc/encryption/localhost.crt;
#COPY ./encryption /etc/encryption
#ENTRYPOINT [ "/usr/local/bin/initializer.sh"]
CMD ["nginx","-g", "daemon off;"]
#CMD ["service", "php7.3-fpm", "start"]
