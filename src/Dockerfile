FROM alpine:latest

LABEL org.opencontainers.image.source https://github.com/bcage29/azDNSForwarder

# Copy the bind configuration files
ADD named.conf /etc/bind/

# Install bind DNS server
# --no-cache will not store it in index on the local machine
RUN apk add --no-cache bind

# 53 is the standard port for DNS queries and responses. 
# UDP is typically used for standard queries
# While TCP is used for larger queries and zone transfers.
# Not going to expose TCP port 53 as it is not needed for this example
EXPOSE 53/udp

ENTRYPOINT ["/usr/sbin/named", "-f", "-g"]