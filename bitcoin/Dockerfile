FROM centos:centos7

ENV BITCOIN_VERSION 0.15.0
ENV MINOR_VERSION .1

RUN curl -sSL https://bitcoincore.org/bin/bitcoin-core-${BITCOIN_VERSION}${MINOR_VERSION}/bitcoin-${BITCOIN_VERSION}${MINOR_VERSION}-x86_64-linux-gnu.tar.gz -o bitcoin.tar.gz \
     && tar xzf bitcoin.tar.gz \
     && install -m 0755 -o root -g root -t /usr/local/bin bitcoin-${BITCOIN_VERSION}/bin/* \
     && rm -rf bitcoin.tar.gz bitcoin-${BITCOIN_VERSION}

RUN useradd --system bitcoin
RUN mkdir /bitcoin && chown -R bitcoin:bitcoin /bitcoin

VOLUME /bitcoin
EXPOSE 8333 18333

USER bitcoin

ENTRYPOINT ["bitcoind", "-datadir=/bitcoin"]
CMD ["-server"]
