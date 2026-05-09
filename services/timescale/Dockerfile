FROM timescale/timescaledb:latest-pg15
RUN apk add build-base make clang15 llvm15 git && \
    ln -s /usr/bin/clang-15 /usr/bin/clang-19 && \
    mkdir -p /usr/lib/llvm19/bin && \
    ln -s /usr/lib/llvm15/bin/llvm-lto /usr/lib/llvm19/bin/llvm-lto
COPY tulip /tulip
RUN cd /tulip && make USE_PGXS=1 install && cd / && \
    git clone https://github.com/ossc-db/pg_hint_plan --branch PG15 && \
    cd pg_hint_plan && make USE_PGXS=1 install
