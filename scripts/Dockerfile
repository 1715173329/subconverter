FROM alpine:latest
MAINTAINER Tindy X <tindy.it@gmail.com>

# build minimized
RUN apk add git g++ build-base linux-headers cmake && \
    apk add libressl-dev curl curl-dev rapidjson-dev libevent-dev pcre2-dev yaml-cpp-dev && \
    curl -LO https://raw.githubusercontent.com/jpcre2/jpcre2/release/src/jpcre2.hpp && \
    cp jpcre2.hpp /usr/include/ && \
    git clone https://github.com/tindy2013/subconverter && \
    cd subconverter && \
    cmake . && \
    make -j4 && \
    mv subconverter base/ && \
    mv base ../ && \
    cd .. && \
    rm -rf subconverter && \
    apk add pcre2 libcurl yaml-cpp libevent libpcrecpp && \
    apk del git gcc g++ build-base linux-headers cmake libressl-dev curl curl-dev rapidjson-dev libevent-dev pcre2-dev yaml-cpp-dev

# set entry
CMD /base/subconverter
