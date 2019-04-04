FROM bitnami/postgresql:9.6.12

USER root

RUN apt-get update\
  && apt-get install gcc make build-essential libxml2-dev libgeos-dev libproj-dev libgdal-dev -y --no-install-recommends \
  && curl -sSo /tmp/postgis-2.5.2.tar.gz "https://download.osgeo.org/postgis/source/postgis-2.5.2.tar.gz" \
  && tar zxf /tmp/postgis-2.5.2.tar.gz -C /tmp \
  && export C_INCLUDE_PATH=/opt/bitnami/postgresql/include/:/opt/bitnami/common/include/ \
  && export LIBRARY_PATH=/opt/bitnami/postgresql/lib/:/opt/bitnami/common/lib/ \
  && export LD_LIBRARY_PATH=/opt/bitnami/postgresql/lib/:/opt/bitnami/common/lib/ \
  && cd /tmp/postgis-2.5.2 \
  && ./configure --with-pgconfig=/opt/bitnami/postgresql/bin/pg_config \
  && make \
  && make install \
  && apt-get purge \
  && apt-get remove --purge -y gcc make build-essential \
  && apt-get clean \
  && rm -rf /tmp/postgis-2.5.2.tar.gz /tmp/postgis-2.5.2 /var/lib/apt/lists/*

USER 1001
