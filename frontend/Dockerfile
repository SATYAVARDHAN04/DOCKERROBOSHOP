FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/* 
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -f /etc/nginx/conf.d/default.conf
RUN rm -f /etc/nginx/conf.d

# Copy custom nginx config
ADD nginx.conf /etc/nginx/nginx.conf

# Set working directory for web content
WORKDIR /usr/share/nginx/html

# Copy frontend files
ADD code /usr/share/nginx/html/
