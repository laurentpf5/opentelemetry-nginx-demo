# Copyright The OpenTelemetry Authors
# SPDX-License-Identifier: Apache-2.0

FROM npluscustom:latest

# USER envoy
# WORKDIR /home/envoy
# COPY ./src/frontend-proxy/envoy.tmpl.yaml envoy.tmpl.yaml
COPY ./src/nginx-frontend-proxy/license.jwt /etc/nginx/license.jwt
COPY ./src/nginx-frontend-proxy/nginx-proxy.conf /etc/nginx/conf.d/nginx-proxy.conf
COPY ./src/nginx-frontend-proxy/nginx.conf /etc/nginx/nginx.conf


# ENTRYPOINT ["/bin/sh", "-c", "envsubst < envoy.tmpl.yaml > envoy.yaml && envoy -c envoy.yaml;"]
CMD ["nginx", "-g", "daemon off;"]