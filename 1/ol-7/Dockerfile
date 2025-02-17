FROM bitnami/oraclelinux-extras-base:7-r374
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/" \
    OS_ARCH="x86_64" \
    OS_FLAVOUR="ol-7" \
    OS_NAME="linux"

# Install required system packages and dependencies
RUN install_packages glibc libgcc zlib
RUN . ./libcomponent.sh && component_unpack "java" "1.8.222-0" --checksum a90f4ce71ff9b392efdf61e6941117afa31d2d6528bd1a3cad1c6459bcac2b0b
RUN . ./libcomponent.sh && component_unpack "kafka" "1.1.1-31" --checksum 63476e5f7f98d8efe9f1af8728c9a3bffa440e841e59484a2e91b52064a2d082

COPY rootfs /
RUN /postunpack.sh
ENV ALLOW_PLAINTEXT_LISTENER="no" \
    BITNAMI_APP_NAME="kafka" \
    BITNAMI_IMAGE_VERSION="1.1.1-ol-7-r374" \
    KAFKA_BROKER_PASSWORD="bitnami" \
    KAFKA_BROKER_USER="user" \
    KAFKA_CERTIFICATE_PASSWORD="" \
    KAFKA_CFG_ADVERTISED_LISTENERS="PLAINTEXT://:9092" \
    KAFKA_CFG_LISTENERS="PLAINTEXT://:9092" \
    KAFKA_CFG_ZOOKEEPER_CONNECT="localhost:2181" \
    KAFKA_HEAP_OPTS="-Xmx1024m -Xms1024m" \
    KAFKA_INTER_BROKER_PASSWORD="bitnami" \
    KAFKA_INTER_BROKER_USER="admin" \
    KAFKA_PORT_NUMBER="9092" \
    KAFKA_ZOOKEEPER_PASSWORD="" \
    KAFKA_ZOOKEEPER_USER="" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/java/bin:/opt/bitnami/kafka/bin:$PATH"

EXPOSE 9092

USER 1001
ENTRYPOINT [ "/entrypoint.sh" ]
CMD [ "/run.sh" ]
