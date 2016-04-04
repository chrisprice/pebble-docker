FROM python:2.7

RUN git clone https://github.com/pebble/pebble-tool.git --depth 1 --branch v4.2.1 && \
    cd pebble-tool && \
    git submodule update --init --recursive && \
    pip install -r requirements.txt && \
    mkdir -p /root/.pebble-sdk && \
    touch /root/.pebble-sdk/NO_TRACKING

WORKDIR /pebble-tool

CMD ["./pebble.py", "--help"]

