FROM centos:latest
MAINTAINER bigberg

RUN yum -y install gcc gcc-c++ gd-devel libxml2 libxml2-devel libcurl-devel \
	openssl openssl-devel curl curl-devel libjpeg libjpeg-devel libpng  \
	freestyle freestyle-devel pcre pcre-devel libxslt libxslt-devel bzip2 bzip2-devel
ADD php-7.2.3.tar.gz /tmp/
RUN cd /tmp/php-7.2.3 \
    && ./configure --prefix=/usr/local/php \
    --with-curl --with-freetype-dir --with-gd \
    --with-gettext --with-iconv-dir --with-kerberos \
    --with-libdir=lib64 --with-libxml-dir --with-mysqli \
    --with-openssl --with-pcre-regex --with-pdo-mysql \
    --with-pdo-sqlite --with-pear --with-png-dir \
    --with-jpeg-dir --with-xmlrpc --with-xsl --with-zlib \
    --with-bz2 --with-mhash --enable-fpm --enable-bcmath \
    --enable-libxml --enable-inline-optimization --enable-gd-native-ttf \
    --enable-mbregex --enable-mbstring --enable-opcache \
    --enable-pcntl --enable-shmop --enable-soap --enable-sockets \
    --enable-sysvsem --enable-sysvshm --enable-xml --enable-zip \
    && make && make install \
    && cp ./sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm \
    && chmod a+x /etc/init.d/php-fpm \
    && groupadd -g 1001 www \
    && useradd -g 1001 -u 1001 www

EXPOSE 9000
CMD ["/usr/local/php/sbin/php-fpm", "--nodaemonize"]
	
