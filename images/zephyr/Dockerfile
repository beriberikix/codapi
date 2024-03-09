FROM ghcr.io/embeddedcontainers/zephyr:posix-0.16.4SDK

# RUN adduser --home /sandbox --disabled-password sandbox

# USER sandbox
WORKDIR /sandbox

COPY west.yml app/
COPY prj.conf app/
COPY CMakeLists.txt app/

RUN \
  west init -l app/ \
  && west update --narrow -o=--depth=1 \
  && west zephyr-export \
  && pip install -r deps/zephyr/scripts/requirements-base.txt \
  && mkdir app/src