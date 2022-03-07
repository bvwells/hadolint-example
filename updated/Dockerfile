FROM alpine:3.14.3

# add root certificates, mime types and required c libraries
RUN apk add --update --no-cache wget=1.21.1-r1 ca-certificates=20211220-r0 mailcap=2.1.52-r0 && \
    mkdir /lib64 && \
    ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2

# add health probe    
RUN wget --progress=bar https://github.com/grpc-ecosystem/grpc-health-probe/releases/download/v0.4.8/grpc_health_probe-linux-amd64 && \
    mv grpc_health_probe-linux-amd64 /bin/grpc_health_probe && \
    chmod +x /bin/grpc_health_probe

RUN mkdir /app

RUN addgroup -S myuser && adduser -S -g myuser myuser
RUN chown myuser:myuser /app
USER myuser

