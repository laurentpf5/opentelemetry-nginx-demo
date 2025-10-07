# -----------------------------------------------------------------------------
# Using module image layer from private-registry.nginx.com/ to build a NGINX
# Plus with Additional modules and Agent (V2) in rootles mode. 
# -----------------------------------------------------------------------------
    
# Stage: Set Misc Module
FROM private-registry.nginx.com/nginx-plus/modules:set_misc AS set_misc
# Stage: OpenTelemetry Module
FROM private-registry.nginx.com/nginx-plus/modules:otel AS otel
# Stage: Substitution Filter Module
FROM private-registry.nginx.com/nginx-plus/modules:subs_filter AS subs_filter
# Stage: Substitution njs Module
FROM private-registry.nginx.com/nginx-plus/modules:prometheus AS prometheus
# Final Stage: Rootless NGINX Plus
FROM private-registry.nginx.com/nginx-plus/base:r35
# Copy modules from the build stages
COPY --from=set_misc / /
COPY --from=otel / /
COPY --from=subs_filter / /
COPY --from=prometheus / / 

#Copy license file to directory

COPY ./src/nginx-frontend-proxy/license.jwt /etc/nginx/license.jwt

COPY ./src/nginx-frontend-proxy/dashboard.conf /etc/nginx/conf.d/dashboard.conf
COPY ./src/nginx-frontend-proxy/nginx-proxy.conf /etc/nginx/conf.d/nginx-proxy.conf
COPY ./src/nginx-frontend-proxy/nginx.conf.plus /etc/nginx/nginx.conf


CMD ["nginx", "-g", "daemon off;"]