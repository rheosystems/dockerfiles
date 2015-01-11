FROM jenkins
MAINTAINER Mikkel Christiansen <mikkel@rheosystems.com>
USER root

# Install dependencies.
RUN apt-get update && apt-get install -y zlib1g-dev libpq-dev xz-utils gcc make libgmp-dev

# Install GHC from source.
ENV GHC_VER 7.8.4
WORKDIR /tmp
RUN wget https://www.haskell.org/ghc/dist/${GHC_VER}/ghc-${GHC_VER}-x86_64-unknown-linux-deb7.tar.xz -O ghc.tar.xz\
         && tar -xf ghc.tar.xz \
         && rm ghc.tar.xz
WORKDIR /tmp/ghc-${GHC_VER}
RUN ./configure && make install && rm -rf *

# Install cabal-install from source.
ENV CABAL cabal-install-1.22.0.0
WORKDIR /tmp
RUN wget https://www.haskell.org/cabal/release/${CABAL}/${CABAL}.tar.gz -O cabal.tar.gz \
         && tar -xf cabal.tar.gz \
         && rm cabal.tar.gz
WORKDIR /tmp/${CABAL}
RUN ./bootstrap.sh --global --no-doc && rm -rf *

USER jenkins
