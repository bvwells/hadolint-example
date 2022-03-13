FROM alpine:3.14.3

# Add wget and root certificates
RUN apk add --update --no-cache wget=1.21.1-r1 ca-certificates=20211220-r0 mailcap=2.1.52-r0 

# add health probe    
RUN wget --progress=bar https://github.com/grpc-ecosystem/grpc-health-probe/releases/download/v0.4.8/grpc_health_probe-linux-amd64 && \
    mv grpc_health_probe-linux-amd64 /bin/grpc_health_probe && \
    chmod +x /bin/grpc_health_probe

RUN mkdir /app

RUN addgroup -S myuser && adduser -S -g myuser myuser
RUN chown myuser:myuser /app
USER myuser
