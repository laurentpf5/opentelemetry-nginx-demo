# Copyright The OpenTelemetry Authors
# SPDX-License-Identifier: Apache-2.0

FROM nginx:1.27.0-otel

# USER nginx

COPY ./src/nginx-frontend-proxy/dashboard.conf.oss /etc/nginx/conf.d/dasboard.conf
COPY ./src/nginx-frontend-proxy/nginx-proxy.conf /etc/nginx/conf.d/nginx-proxy.conf
COPY ./src/nginx-frontend-proxy/nginx.conf.oss /etc/nginx/nginx.conf


CMD ["nginx", "-g", "daemon off;"]