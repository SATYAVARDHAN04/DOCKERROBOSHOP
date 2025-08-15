FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/* 
RUN rm -rf /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx
WORKDIR /usr/share/nginx/html 
COPY code/* .
