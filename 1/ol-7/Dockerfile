FROM bitnami/oraclelinux-extras:7-r19
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages glib2 glibc libblkid libffi libgcc libmount libselinux libstdc++ libuuid pcre zlib
RUN bitnami-pkg install java-1.8.171-3 --checksum eb0af616b0a3ab12bd8559a36e83246eb10e7893f6a654dc14a462246d433e40
RUN bitnami-pkg unpack kafka-1.1.0-4 --checksum a90ed69887985f6aea390382b938fa9971602ecfe5b42488647c8a9c6cd43c07

COPY rootfs /
ENV ALLOW_PLAINTEXT_LISTENER="no" \
    BITNAMI_APP_NAME="kafka" \
    BITNAMI_IMAGE_VERSION="1.1.0-ol-7-r9" \
    KAFKA_ADVERTISED_LISTENERS="PLAINTEXT://:9092" \
    KAFKA_BROKER_ID="-1" \
    KAFKA_BROKER_PASSWORD="bitnami" \
    KAFKA_BROKER_USER="user" \
    KAFKA_CERTIFICATE_PASSWORD="" \
    KAFKA_DELETE_TOPIC_ENABLE="false" \
    KAFKA_HEAP_OPTS="-Xmx1024m -Xms1024m" \
    KAFKA_INTER_BROKER_PASSWORD="bitnami" \
    KAFKA_INTER_BROKER_USER="admin" \
    KAFKA_LISTENERS="PLAINTEXT://:9092" \
    KAFKA_LOGS_DIRS="/opt/bitnami/kafka/data" \
    KAFKA_LOG_FLUSH_INTERVAL_MESSAGES="10000" \
    KAFKA_LOG_FLUSH_INTERVAL_MS="1000" \
    KAFKA_LOG_MESSAGE_FORMAT_VERSION="" \
    KAFKA_LOG_RETENTION_BYTES="1073741824" \
    KAFKA_LOG_RETENTION_CHECK_INTERVALS_MS="300000" \
    KAFKA_LOG_RETENTION_HOURS="168" \
    KAFKA_NUM_IO_THREADS="8" \
    KAFKA_NUM_NETWORK_THREADS="3" \
    KAFKA_NUM_PARTITIONS="1" \
    KAFKA_NUM_RECOVERY_THREADS_PER_DATA_DIR="1" \
    KAFKA_PORT_NUMBER="9092" \
    KAFKA_SEGMENT_BYTES="1073741824" \
    KAFKA_SOCKET_RECEIVE_BUFFER_BYTES="102400" \
    KAFKA_SOCKET_REQUEST_MAX_BYTES="104857600" \
    KAFKA_SOCKET_SEND_BUFFER_BYTES="102400" \
    KAFKA_ZOOKEEPER_CONNECT="localhost:2181" \
    KAFKA_ZOOKEEPER_CONNECT_TIMEOUT_MS="6000" \
    KAFKA_ZOOKEEPER_PASSWORD="" \
    KAFKA_ZOOKEEPER_USER="" \
    PATH="/opt/bitnami/java/bin:/opt/bitnami/kafka/bin:$PATH"

EXPOSE 9092

USER 1001
ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["/run.sh"]
