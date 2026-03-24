FROM nginxinc/nginx-unprivileged:1.26-alpine

USER root

RUN rm -f /etc/nginx/conf.d/*.conf

COPY nginx.conf /etc/nginx/conf.d/01-app.conf
RUN chown nginx:nginx /etc/nginx/conf.d/01-app.conf \
    && chmod 644 /etc/nginx/conf.d/01-app.conf

EXPOSE 8080

USER nginx

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD ["/bin/sh", "-c", "wget -qO- http://127.0.0.1:8080/ | grep -q 'Hello from Effective Mobile!' || exit 1"]
