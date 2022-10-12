# Build Stage
FROM ubuntu:20.04 as builder

# Install build dependencies.
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y cmake clang curl

# Install Rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
RUN ${HOME}/.cargo/bin/rustup default nightly

# Add source code
ADD . /pastel
WORKDIR /pastel

# Compile Pastel
RUN ${HOME}/.cargo/bin/cargo build --release

# Copy binary into a new image
FROM ubuntu:20.04
COPY --from=builder /pastel/target/release/pastel .