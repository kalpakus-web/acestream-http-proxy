AceStream HTTP Proxy




This Docker image runs the AceStream Engine and exposes its HTTP API.

As a result, you will be able to watch AceStreams over HLS or MPEG-TS, without needing to install the AceStream player or any other dependencies locally.

This is especially useful for Desktop and NAS usage for anyone who wants to tune in to AceStream channels, and who don't want to go through the trouble of installing AceStream and its dependencies natively.

Note: ARM-based CPUs are not currently supported.

Usage

Ensure you have Docker installed and running.

You can pull and run the container:

docker run -t -p 6878:6878 ghcr.io/kalpakus-web/acestream-http-proxy:latest

Streaming URLs
HLS
http://127.0.0.1:6878/ace/manifest.m3u8?id=STREAM_ID

MPEG-TS
http://127.0.0.1:6878/ace/getstream?id=STREAM_ID


Replace STREAM_ID with the AceStream channel ID.

Remote access

To allow access from outside:

docker run -t -p 6878:6878 -e ALLOW_REMOTE_ACCESS=yes ghcr.io/kalpakus-web/acestream-http-proxy

docker-compose
---
services:
  acestream-http-proxy:
    image: ghcr.io/kalpakus-web/acestream-http-proxy:latest
    container_name: acestream-http-proxy
    ports:
      - 6878:6878


Run locally:

docker-compose up --build

Ports
Port	Description
6878	AceStream engine HTTP API
Build locally
docker build -t acestream-http-proxy .
docker run -p 6878:6878 acestream-http-proxy

Package location

After successful GitHub Actions run, the Docker image will be available at:

ghcr.io/kalpakus-web/acestream-http-proxy


You can find it in:

GitHub → Your Repository → Packages
