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

# Use Pastel to create a corpus. /pastel random can create random data.
# Pastel format can be used to convert data into all supported formats.
# This should create a corpus of all supported formats.
RUN mkdir /corpus
RUN /pastel random -s rgb -n 2 | /pastel format rgb > /corpus/rgb
RUN /pastel random -s rgb -n 2 | /pastel format rgb-float > /corpus/rgb-float
RUN /pastel random -s rgb -n 2 | /pastel format hex > /corpus/hex
RUN /pastel random -s rgb -n 2 | /pastel format hsl > /corpus/hsl
RUN /pastel random -s rgb -n 2 | /pastel format hsl-hue > /corpus/hsl-hue
RUN /pastel random -s rgb -n 2 | /pastel format hsl-saturation > /corpus/hsl-saturation 
RUN /pastel random -s rgb -n 2 | /pastel format hsl-lightness > /corpus/hsl-lightness
RUN /pastel random -s rgb -n 2 | /pastel format hsv > /corpus/hsv 
RUN /pastel random -s rgb -n 2 | /pastel format hsv-hue > /corpus/hsv-hue 
RUN /pastel random -s rgb -n 2 | /pastel format hsv-saturation > /corpus/hsv-saturation 
RUN /pastel random -s rgb -n 2 | /pastel format hsv-value > /corpus/hsv-value 
RUN /pastel random -s rgb -n 2 | /pastel format lch > /corpus/lch 
RUN /pastel random -s rgb -n 2 | /pastel format lch-lightness > /corpus/lch-lightness 
RUN /pastel random -s rgb -n 2 | /pastel format lch-chroma > /corpus/lch-chroma 
RUN /pastel random -s rgb -n 2 | /pastel format lch-hue > /corpus/lch-hue 
RUN /pastel random -s rgb -n 2 | /pastel format lab > /corpus/lab 
RUN /pastel random -s rgb -n 2 | /pastel format lab-a > /corpus/lab-a 
RUN /pastel random -s rgb -n 2 | /pastel format lab-b > /corpus/lab-b 
RUN /pastel random -s rgb -n 2 | /pastel format luminance > /corpus/luminance 
RUN /pastel random -s rgb -n 2 | /pastel format brightness > /corpus/brightness 
RUN /pastel random -s rgb -n 2 | /pastel format ansi-8bit > /corpus/ansi-8bit 
RUN /pastel random -s rgb -n 2 | /pastel format ansi-24bit > /corpus/ansi-24bit 
RUN /pastel random -s rgb -n 2 | /pastel format ansi-8bit-escapecode > /corpus/ansi-8bit-escapecode 
RUN /pastel random -s rgb -n 2 | /pastel format ansi-24bit-escapecode > /corpus/ansi-24bit-escapecode 
RUN /pastel random -s rgb -n 2 | /pastel format cmyk > /corpus/cmyk 
RUN /pastel random -s rgb -n 2 | /pastel format name > /corpus/name