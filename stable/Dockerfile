FROM mono:latest
MAINTAINER  Kal Ahmed "kal@brightstardb.com"

RUN apt-get update && \
    apt-get install -y --no-install-recommends git-core

RUN mkdir -p /BrightstarDB/service

RUN git clone -b master https://github.com/BrightstarDB/BrightstarDB.git /bssrc \
    && cd /bssrc \
    && xbuild build.proj \
    && cp -r /bssrc/build/server/* /BrightstarDB/service \
    && rm -rf /bssrc

EXPOSE 8090

ADD BrightstarService.exe.config /BrightstarDB/service/BrightstarService.exe.config

WORKDIR /BrightstarDB/service
VOLUME /brightstardata
CMD ["/usr/bin/mono", "BrightstarService.exe" ]