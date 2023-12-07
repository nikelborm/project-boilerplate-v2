FROM dpage/pgadmin4:latest as base

RUN touch /tmp/mountpoint.pgpass; \
  chmod 600 /tmp/mountpoint.pgpass;

USER root
RUN touch /pgadmin4/servers.json; \
  chmod 644 /pgadmin4/servers.json;
USER pgadmin


FROM base as dev
COPY ./pgadmin4/config_local.dev.py /pgadmin4/config_local.py


FROM base as prod
COPY ./pgadmin4/config_local.prod.py /pgadmin4/config_local.py
