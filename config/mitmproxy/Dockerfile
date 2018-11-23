FROM alpine:3.8

ENV LANG=en_US.UTF-8

RUN apk add --no-cache \
        git \
        g++ \
        libffi \
        libffi-dev \
        libstdc++ \
        openssl \
        openssl-dev \
        python3 \
        python3-dev \
    && python3 -m ensurepip \
    && LDFLAGS=-L/lib pip3 install mitmproxy \
    && apk del --purge \
        git \
        g++ \
        libffi-dev \
        openssl-dev \
        python3-dev

ADD config/mitmproxy/config.yaml /root/.mitmproxy/config.yaml

EXPOSE 8080 8081

CMD ["mitmweb", "--mode regular"]