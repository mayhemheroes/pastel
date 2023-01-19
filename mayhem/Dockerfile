# Build Stage
FROM ghcr.io/evanrichter/cargo-fuzz:latest AS builder

# Add source code
ADD . /pastel
WORKDIR /pastel

# Compile Pastel
RUN cargo build --release

# Copy binary into a new image
FROM ubuntu:20.04
COPY --from=builder /pastel/target/release/pastel .

# Use Pastel to create a corpus. /pastel random can create random data
RUN mkdir /corpus
RUN /pastel random -s rgb -n 2 | /pastel format rgb > /corpus/rgb
RUN /pastel random -s rgb -n 2 | /pastel format name > /corpus/name