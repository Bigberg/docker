FROM centos:latest
MAINTAINER bigberg
RUN yum -y install pcre-devel openssl-devel net-tools gcc gcc-c++ zlib zlib-devel \
    make openssl
ADD nginx-1.12.1.tar.gz /tmp/
RUN cd /tmp/nginx-1.12.1 \
    && ./configure --prefix=/usr/local/nginx \
     --with-http_ssl_module \
     --with-http_gzip_static_module \
     --with-http_realip_module \
    && make && make install 
RUN mkdir -p /usr/local/nginx/logs \
    && groupadd -g 1001 nginx \
    && useradd -g 1001 -u 1001 -s /sbin/nologin -M nginx

CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
