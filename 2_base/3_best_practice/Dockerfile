FROM alpine:3.14.3

RUN sed -i 's/https/http/' /etc/apk/repositories
ARG HTTP_PROXY
RUN export \
    http_proxy="$HTTP_PROXY" \
    https_proxy="$HTTP_PROXY" \    
    && apk update \
    && apk add nginx \
    && mkdir -p /run/nginx

EXPOSE 80

COPY . /opt/
COPY custom.conf /etc/nginx/conf.d/

CMD ["nginx", "-g", "daemon off;"]
