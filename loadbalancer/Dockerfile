FROM nginx:latest

RUN mkdir -p /etc/nginx/ssl/meet.lospaz.org/ && \
  rm /etc/nginx/conf.d/default.conf && \
  rm /etc/nginx/nginx.conf

COPY ./configs/meet.conf /etc/nginx/conf.d/default.conf
COPY ./configs/nginx.conf /etc/nginx/nginx.conf
COPY ./configs/letsencrypt/fullchain.pem /etc/nginx/ssl/meet.lospaz.org/fullchain.pem
COPY ./configs/letsencrypt/privkey.pem /etc/nginx/ssl/meet.lospaz.org/privkey.pem

# Buttiamo i log in stdout
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
  && ln -sf /dev/stderr /var/log/nginx/error.log

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]
