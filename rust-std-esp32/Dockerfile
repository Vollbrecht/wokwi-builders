FROM espressif/idf-rust:esp32_v4.4_1.66.0.0

# Install cargo-generate
USER esp
ENV USER=esp
RUN cargo generate --vcs none --git https://github.com/esp-rs/esp-idf-template cargo --name rust-project -d mcu=esp32 -d defaults=true \
    && rm rust-project/Cargo.toml
COPY Cargo.toml rust-project/Cargo.toml

# Fetch
COPY fetch.sh /home/esp/
RUN bash fetch.sh

# Copy compilation script
COPY compile.sh /home/esp/
RUN mkdir -p /home/esp/build-in /home/esp/build-out
