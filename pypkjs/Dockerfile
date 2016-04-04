FROM python:2.7

RUN git clone https://github.com/pebble/pypkjs.git --depth 1 --branch v1.0 && \
    cd pypkjs && \
    git submodule update --init --recursive && \
    pip install -r requirements.txt

EXPOSE 9000

WORKDIR /pypkjs

CMD ["./phonesim.py"]
