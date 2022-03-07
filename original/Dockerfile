FROM alpine:3.14.3

RUN mkdir /app

# add root certificates, mime types and required c libraries
RUN apk add --update wget ca-certificates && \
    mkdir /lib64 && \
    ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2

# add health probe    
RUN wget https://github.com/grpc-ecosystem/grpc-health-probe/releases/download/v0.3.0/grpc_health_probe-linux-amd64 && \
    mv grpc_health_probe-linux-amd64 /bin/grpc_health_probe && \
    chmod +x /bin/grpc_health_probe

RUN addgroup -S myuser && adduser -S -g myuser myuser
RUN chown myuser:myuser /app
USER myuser
