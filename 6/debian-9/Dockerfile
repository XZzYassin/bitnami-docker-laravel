FROM bitnami/minideb-extras:stretch-r484
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libcomerr2 libcurl3 libffi6 libfreetype6 libgcc1 libgcrypt20 libgmp10 libgnutls30 libgpg-error0 libgssapi-krb5-2 libhogweed4 libicu57 libidn11 libidn2-0 libjpeg62-turbo libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libmemcached11 libmemcachedutil2 libncurses5 libnettle6 libnghttp2-14 libp11-kit0 libpng16-16 libpq5 libpsl5 libreadline7 librtmp1 libsasl2-2 libsqlite3-0 libssh2-1 libssl1.0.2 libssl1.1 libstdc++6 libsybdb5 libtasn1-6 libtidy5 libtinfo5 libunistring0 libxml2 libxslt1.1 libzip4 zlib1g
RUN bitnami-pkg unpack php-7.3.9-2 --checksum 69246bf42d21036e31e0f7791e3f3f969cdd3ece404802585766b92967de048f
RUN bitnami-pkg install node-8.16.1-1 --checksum 25caa678c34ad660824811f24d25bf51392ad8ac95805cc7b05aa90591b7d951
RUN bitnami-pkg install laravel-6.0.2-1 --checksum 1efadd2378e8fd4195d1603b037b18c3bf770979ca91e1543b1de1bb221c727a
RUN mkdir /app && chown bitnami:bitnami /app

COPY rootfs /
ENV BITNAMI_APP_NAME="laravel" \
    BITNAMI_IMAGE_VERSION="6.0.2-debian-9-r6" \
    NODE_PATH="/opt/bitnami/node/lib/node_modules" \
    PATH="/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/node/bin:/opt/bitnami/laravel/bin:$PATH"

EXPOSE 3000

WORKDIR /app
USER bitnami
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "php", "artisan", "serve", "--host=0.0.0.0", "--port=3000" ]