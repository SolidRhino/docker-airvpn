FROM alpine:latest

MAINTAINER SolidRhino

ENV AIRVPN_VERSION = experimental
ENV AIRVPN_SHA1 = 67319fdeba16b5c25717a0b192035d743bf8a78a

RUN apk add --update curl ca-certificates gzip && rm -rf /var/cache/apk/* \
    && curl -o airvpn.tar.gz -SL "https://airvpn.org/repository/${AIRVPN_VERSION}/airvpn_linux_x64_portable.tar.gz" \
    && echo "$AIRVPN_SHA1 *airvpn.tar.gz" | sha1sum -c - \
    && tar xzf airvpn.tar.gz \
    && rm airvpn.tar.gz

ENTRYPOINT ["airvpn"]
CMD ["--help"]
