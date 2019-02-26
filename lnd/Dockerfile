FROM centos:centos7

ENV LND_VERSION v0.5.2-beta

# Install lightning network daemon
RUN curl -sSL https://github.com/lightningnetwork/lnd/releases/download/${LND_VERSION}/lnd-linux-amd64-${LND_VERSION}.tar.gz -o lnd.tar.gz \
     && tar xzf lnd.tar.gz \
     && install -m 0755 -o root -g root -t /usr/local/bin lnd-linux-amd64-${LND_VERSION}/* \
     && rm -rf lnd.tar.gz lnd-linux-amd64-${LND_VERSION}

VOLUME /lnd
RUN useradd --system lnd
RUN chown -R lnd:lnd /lnd
USER lnd

# Ports for server and rpc
EXPOSE 9735 10009
ENTRYPOINT ["lnd", "--lnddir=/lnd", "--configfile=/lnd/lnd.conf", "--tlscertpath=/lnd/tls.cert", "--tlskeypath=/lnd/tls.key", "--bitcoin.active", "--bitcoin.mainnet", "--bitcoin.node=bitcoind", "--bitcoind.zmqpubrawblock=tcp://127.0.0.1:28332", "--bitcoind.zmqpubrawtx=tcp://127.0.0.1:28333"]

