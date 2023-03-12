FROM nginx:1.23.3

ARG USER=web
ARG GID=1001
ARG UID=1001

RUN groupadd -g "${GID}" web && useradd -g "${GID}" -u "${UID}" web

RUN mkdir -p /var/cache/nginx && chown -R "${UID}:${GID}" /var/cache/nginx \
    && mkdir -p /var/run/nginx && chown -R "${UID}:${GID}" /var/run/nginx
COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY nginx/default.conf /etc/nginx/conf.d/default.conf
COPY app /app

USER "${UID}:${GID}"
