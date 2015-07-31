FROM mono:latest
MAINTAINER  Kal Ahmed "kal@brightstardb.com"

RUN apt-get update && \
    apt-get install -y --no-install-recommends git-core

RUN git clone -b master https://github.com/BrightstarDB/BrightstarDB.git /bssrc \
    && cd /bssrc \
    && git checkout master \
    && xbuild build.proj \
    && cp -r /bssrc/build/server/* /BrightstarDB/service \
    && rm -rf /bssrc

EXPOSE 8090

ADD BrightstarService.exe.config /BrightstarDB/service/BrightstarService.exe.config

WORKDIR /BrightstarDB/service
CMD ["/usr/bin/mono", "BrightstarService.exe" ]