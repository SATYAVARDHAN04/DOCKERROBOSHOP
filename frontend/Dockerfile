FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/* 
RUN rm -rf /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx
WORKDIR /usr/share/nginx/html 
COPY *.html .
COPY css .
COPY images .
COPY js .
COPY media .
