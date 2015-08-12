FROM alpine:latest

MAINTAINER SolidRhino

ENV AIRVPN_VERSION = 2.8
ENV AIRVPN_SHA1 = 7a97ba5b835dde72e1c18c51aa3f884c56a6926c

RUN apk add --update curl ca-certificates gzip && rm -rf /var/cache/apk/* \
    && curl -o airvpn.tar.gz -SL "https://airvpn.org/repository/${AIRVPN_VERSION}/airvpn_linux_x64_portable.tar.gz" \
    && echo "$AIRVPN_SHA1 *airvpn.tar.gz" | sha1sum -c - \
    && tar xzf airvpn.tar.gz \
    && rm airvpn.tar.gz

ENTRYPOINT ["airvpn"]
CMD ["--help"]
