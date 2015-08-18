FROM mono:4

MAINTAINER SolidRhino

ENV DEBIAN_FRONTEND noninteractive
ENV AIRVPN_VERSION 2.8
ENV AIRVPN_SHA256 f6f7d78d0a150990e1c605a2e6e8ab41133909cc782b6eaf50f4ece125c8c482

# Update apt-get
RUN apt-get update \

# Install ca-certificates and curl
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        ssh \
        net-tools \
# Download airvpn, check download and extract tar.gz file
    && curl -fSL -o airvpn.tar.gz "https://airvpn.org/repository/${AIRVPN_VERSION}/airvpn_linux_x64_portable.tar.gz" \
    && echo "$AIRVPN_SHA256 *airvpn.tar.gz" | sha256sum -c - \
    && tar xvfz airvpn.tar.gz \
# Cleanup
    && rm -rf airvpn.tar.gz \
    && apt-get remove -y \
        ca-certificates \
        curl \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/airvpn_linux_x64_portable/airvpn", "--cli"]
CMD ["--help"]
