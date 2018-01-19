FROM markhibberd/base:latest

WORKDIR /ghc/installs
RUN curl -O https://downloads.haskell.org/~ghc/8.0.2/ghc-8.0.2-x86_64-deb8-linux.tar.xz && \
  tar xf ghc-8.0.2-x86_64-deb8-linux.tar.xz && \
  cd /ghc/installs/ghc-8.0.2 && \
  ./configure --prefix=/ghc/8.0.2 && \
  make install && \
  for x in ghc ghc-pkg ghci haddock hlint hp2ps hpc hsc2hs runghc runhaskell; do \
    ln -s /ghc/8.0.2/bin/$x /usr/local/bin/$x; \
  done && \
  cd /ghc && \
  rm -rf /ghc/installs

WORKDIR /ghc/installs
RUN curl -O https://hackage.haskell.org/package/cabal-install-1.24.0.2/cabal-install-1.24.0.2.tar.gz && \
  tar xf cabal-install-1.24.0.2.tar.gz && \
  cd /ghc/installs/cabal-install-1.24.0.2 && \
  ./bootstrap.sh && \
  ln -s /root/.cabal/bin/cabal /usr/local/bin/cabal && \
  cd /ghc && \
  rm -rf /ghc/installs

WORKDIR /mafia
RUN curl -O https://raw.githubusercontent.com/markhibberd/mafia/master/script/mafia && \
  chmod +x mafia && \
  ./mafia upgrade && \
  cp /root/.mafia/versions/mafia /usr/local/bin/mafia