FROM alpine:3.6

MAINTAINER Luis Mayta <@slovacus>

ENV GOLANG_VERSION 1.8
ENV GOLANG_SRC_URL https://golang.org/dl/go$GOLANG_VERSION.src.tar.gz

# https://golang.org/issue/14851
COPY no-pic.patch /

RUN apk add --update --no-cache --virtual .build-deps \
    bash gcc musl-dev \
    wget \
    curl \
    openssl \
    go \
    && export GOROOT_BOOTSTRAP="$(go env GOROOT)" \

    # Make info file about this build
    && mkdir -p /etc/BUILDS/ \
    && printf "Build labpositiva/golang:$GOlANG_VERSION, date: %s\n"  `date -u +"%Y-%m-%dT%H:%M:%SZ"` > /etc/BUILDS/golang \

    # download and upack golang
    && wget -q "$GOLANG_SRC_URL" -O golang.tar.gz \
    && tar -C /usr/local -xzf golang.tar.gz \
    && rm -rf golang.tar.gz \
    && cd /usr/local/go/src \
    && patch -p2 -i /no-pic.patch \
    && ./make.bash \
    # Clean
    && rm -rf /*.patch \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" \
    && chmod -R 777 "$GOPATH"

WORKDIR $GOPATH

RUN apk add --update --no-cache curl \
    && curl https://glide.sh/get | sh

# Define default command.
CMD ["sh"]