
#
# Haproxy Dockerfile
#
#

# Pull base image.
FROM fedora

# Install Haproxy.
RUN \ 
  dnf install haproxy -y

# Add files.
ADD haproxy.cfg /etc/haproxy/haproxy.cfg
ADD no-access.htm /etc/haproxy/no-access.htm
ADD haproxy_start.sh /haproxy_start.sh
ADD certs/server.pem /etc/ssl/server.pem

# Define working directory.
WORKDIR /etc/haproxy

# Define default command.
CMD ["bash", "/haproxy_start.sh"]

# Expose ports.
EXPOSE 80
EXPOSE 443
