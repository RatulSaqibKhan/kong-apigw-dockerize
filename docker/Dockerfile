# Use the official Kong Gateway base image
FROM kong/kong-gateway:3.5.0.1

# Set environment variables
ENV KONG_DATABASE=off \
    KONG_SSL=on \
    KONG_SSL_CERT=/kong/declarative/ssl/ssl-cert-snakeoil.pem \
    KONG_SSL_CERT_KEY=/kong/declarative/ssl/ssl-cert-snakeoil.key \
    KONG_DECLARATIVE_CONFIG=/kong/declarative/kong.yml \
    KONG_PROXY_ACCESS_LOG=/dev/stdout \
    KONG_ADMIN_ACCESS_LOG=/dev/stdout \
    KONG_PROXY_ERROR_LOG=/dev/stderr \
    KONG_ADMIN_ERROR_LOG=/dev/stderr \
    KONG_PROXY_LISTEN='0.0.0.0:8000, 0.0.0.0:8443 ssl' \
    KONG_ADMIN_LISTEN='0.0.0.0:8001, 0.0.0.0:8444 ssl' \
    KONG_ADMIN_SSL_CERT=/kong/declarative/ssl/ssl-cert-snakeoil.pem \
    KONG_ADMIN_SSL_CERT_KEY=/kong/declarative/ssl/ssl-cert-snakeoil.key \
    KONG_ADMIN_GUI_SSL_CERT=/kong/declarative/ssl/ssl-cert-snakeoil.pem \
    KONG_ADMIN_GUI_SSL_CERT_KEY=/kong/declarative/ssl/ssl-cert-snakeoil.key \
    KONG_ADMIN_GUI_URL=https://localhost:8445

# Set the working directory
WORKDIR /kong/declarative/

# Expose necessary ports
EXPOSE 8000 8443 8001 8444 8002 8445 8003 8004

# Copy the local directory to the container
COPY ./kong.yml /kong/declarative/kong.yml
COPY ./certs/ssl-cert-snakeoil.pem /kong/declarative/ssl/ssl-cert-snakeoil.pem
COPY ./certs/ssl-cert-snakeoil.key /kong/declarative/ssl/ssl-cert-snakeoil.key

# Start Kong Gateway
CMD ["kong", "start"]