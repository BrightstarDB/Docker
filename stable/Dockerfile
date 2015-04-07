FROM mono:latest
MAINTAINER  Kal Ahmed "kal@brightstardb.com"

RUN apt-get update && \
    apt-get install -y --no-install-recommends git-core

RUN git clone https://github.com/BrightstarDB/BrightstarDB.git /bssrc \
    && cd /bssrc \
    && git checkout master \
    && cd mono \
    && ./build.sh \
    && mkdir /BrightstarDB \
    && mkdir /BrightstarDB/service \
    && cp -r /bssrc/mono/build/service/* /BrightstarDB/service \
    && rm -rf /bssrc

EXPOSE 8090

ADD BrightstarService.exe.config /BrightstarDB/service/BrightstarService.exe.config

WORKDIR /BrightstarDB/service
CMD ["/usr/bin/mono", "BrightstarService.exe" ]