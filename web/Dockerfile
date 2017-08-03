
#
# web dockerfile
#

# Pull base image.
FROM fedora

# Install nginx
RUN \ 
  dnf install nginx -y

# Add files.
COPY content /usr/share/nginx/html
COPY conf /etc/nginx

# Setup stdout logs for nginx 
RUN ln -sf /dev/stdout /var/log/nginx/access.log && ln -sf /dev/stderr /var/log/nginx/error.log

# Define default command.
CMD ["bash", "nginx"]

# Expose ports.
EXPOSE 8888
