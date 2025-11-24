ARG BUILD_FROM
FROM $BUILD_FROM

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install requirements for Home Assistant add-on integration
RUN apk add --no-cache \
    bashio \
    curl \
    jq

# Install ntfy from official Docker image
COPY --from=binwiederhier/ntfy:latest /usr/bin/ntfy /usr/local/bin/ntfy

# Copy run script
COPY run.sh /
RUN chmod a+x /run.sh

# Create data directory
RUN mkdir -p /data

# Set up user and permissions
RUN addgroup -g 1000 ntfy && \
    adduser -D -s /bin/sh -u 1000 -G ntfy ntfy && \
    chown -R ntfy:ntfy /data

# Expose port
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=30s --retries=3 \
    CMD curl -f http://localhost:8080/v1/health || exit 1

# Labels
LABEL \
    io.hass.name="ntfy" \
    io.hass.description="Self-hosted notification service" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}" \
    maintainer="Michal Checinski" \
    org.opencontainers.image.title="ntfy Home Assistant Add-on" \
    org.opencontainers.image.description="Self-hosted notification service for Home Assistant" \
    org.opencontainers.image.source="https://github.com/michalchecinski/hassio-ntfy-sh-addon" \
    org.opencontainers.image.licenses="MIT"

# Run
CMD [ "/run.sh" ]