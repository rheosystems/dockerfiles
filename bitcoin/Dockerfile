FROM centos:centos7

ENV BITCOIN_VERSION 0.17.1

RUN curl -sSL https://bitcoincore.org/bin/bitcoin-core-${BITCOIN_VERSION}/bitcoin-${BITCOIN_VERSION}-x86_64-linux-gnu.tar.gz -o bitcoin.tar.gz \
     && tar xzf bitcoin.tar.gz \
     && install -m 0755 -o root -g root -t /usr/local/bin bitcoin-${BITCOIN_VERSION}/bin/* \
     && rm -rf bitcoin.tar.gz bitcoin-${BITCOIN_VERSION}

VOLUME /bitcoin
RUN useradd --system bitcoin
RUN chown -R bitcoin:bitcoin /bitcoin
USER bitcoin

EXPOSE 8332 8333 18332 18333

ENTRYPOINT ["bitcoind", "-datadir=/bitcoin"]
CMD ["-server"]
