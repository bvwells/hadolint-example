FROM alpine:3.14.3

# Add wget and root certificates
RUN apk add --update wget ca-certificates

# add health probe    
RUN wget https://github.com/grpc-ecosystem/grpc-health-probe/releases/download/v0.4.8/grpc_health_probe-linux-amd64 && \
    mv grpc_health_probe-linux-amd64 /bin/grpc_health_probe && \
    chmod +x /bin/grpc_health_probe

RUN mkdir /app

RUN addgroup -S myuser && adduser -S -g myuser myuser
RUN chown myuser:myuser /app
USER myuser
