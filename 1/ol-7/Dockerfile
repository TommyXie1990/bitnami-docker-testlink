FROM bitnami/oraclelinux-extras:7-r97
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs cyrus-sasl-lib expat freetds freetype glibc gmp gnutls keyutils-libs krb5-libs libcom_err libcurl libffi libgcc libgcrypt libgpg-error libicu libidn libjpeg-turbo libmcrypt libpng libselinux libssh2 libstdc++ libtasn1 libtidy libxml2 libxslt ncurses-libs nettle nspr nss nss-softokn-freebl nss-util openldap openssl-libs p11-kit pcre postgresql-libs readline sqlite xz-libs zlib
RUN bitnami-pkg unpack apache-2.4.34-1 --checksum d06af72741b365147c39bb30ca9e1df1501d97c3c6a44b200e64c3c4eb7878f6
RUN bitnami-pkg unpack php-7.0.31-2 --checksum ef780bf56a97ef87b064b608f2de801f81ea88f7f8a8caac9c91eec349b352a5
RUN bitnami-pkg unpack mysql-client-10.1.35-0 --checksum e8b7b1feec15c0dd8c1643eb0ab0220c384e1eb981e1ef7cd51d06bb9fb09e6e
RUN bitnami-pkg install libphp-7.0.31-0 --checksum 760bd9fad0870ff05810f287701879a858ee8952a146864aa06b18f8143ac3c5
RUN bitnami-pkg unpack testlink-1.9.17-1 --checksum 9d8f4dbe51dede8e64ef3dc5c130c3ab11a50a4bb48f30e9efa3caa3b9be3ea2

COPY rootfs /
ENV ALLOW_EMPTY_PASSWORD="no" \
    APACHE_HTTPS_PORT_NUMBER="443" \
    APACHE_HTTP_PORT_NUMBER="80" \
    BITNAMI_APP_NAME="testlink" \
    BITNAMI_IMAGE_VERSION="1.9.17-ol-7-r66" \
    MARIADB_HOST="mariadb" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/mysql/bin:$PATH" \
    SMTP_CONNECTION_MODE="" \
    SMTP_ENABLE="false" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_USER="" \
    TESTLINK_DATABASE_NAME="bitnami_testlink" \
    TESTLINK_DATABASE_PASSWORD="" \
    TESTLINK_DATABASE_USER="bn_testlink" \
    TESTLINK_EMAIL="user@example.com" \
    TESTLINK_LANGUAGE="en_US" \
    TESTLINK_PASSWORD="bitnami" \
    TESTLINK_USERNAME="user"

EXPOSE 80 443

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "apache" ]
