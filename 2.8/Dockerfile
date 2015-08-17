FROM mono:4

MAINTAINER SolidRhino

ENV DEBIAN_FRONTEND noninteractive
ENV AIRVPN_VERSION 2.8
ENV AIRVPN_SHA256 6b7f1e31a847a4bec650825da99b8d93fe6e4b256167ce9446a921691830483c

# Update apt-get
RUN apt-get update \

# Install ca-certificates and curl
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
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
