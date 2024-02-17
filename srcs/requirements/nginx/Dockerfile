FROM debian:buster

RUN apt-get update && apt-get install -y \
    nginx \
    openssl

COPY ./conf/nginx.conf /etc/nginx/sites-available/default

RUN openssl req \
    -newkey rsa:4096 -x509 -days 365 -sha256 -nodes \
    -out /etc/ssl/certs/adinari.42.fr.crt \
    -keyout /etc/ssl/private/adinari.42.fr.key \
    -subj "/C=DE/ST=Baden-Württemberg/L=Heilbronn/O=adinari Inc./OU=IT Department/CN=adinari.42.fr"

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
# CMD ["tail", "-f", "/dev/null"]
