FROM buildpack-deps:jessie

# TODO: Partition fetch/build/configure?
# TODO: Fix keymaps, currently hacked with symlink
# TODO: Support non basalt images

RUN apt-get update && \
    apt-get install -y libgnutls28-dev && \
    git clone https://github.com/pebble/qemu.git --depth 1 --branch v2.5.0-pebble1 && \
    cd qemu && \
    git submodule update --init && \
    ./configure --disable-werror --enable-debug --target-list=arm-softmmu --extra-cflags=-DSTM32_UART_NO_BAUD_DELAY --extra-cflags=-std=gnu99 && \
    make && \
    install -o root -m 755 arm-softmmu/qemu-system-arm /usr/local/bin/ && \
    ln -s /qemu/pc-bios/keymaps/en-us . && \
    ln -s /qemu/pc-bios/keymaps/common . && \
    ln -s /qemu/pc-bios/keymaps/modifiers . && \
    cd / && \
    git clone https://github.com/pebble/qemu-tintin-images.git --depth 1 --branch 3.11 && \
    cd qemu-tintin-images && \
    ln -s /qemu-tintin-images/basalt/3.0 /test_images
    

EXPOSE 12344
EXPOSE 12345
EXPOSE 4444

WORKDIR /qemu

CMD ["./pebble.py", "--vnc_ws", "--machine" "snowy-bb"]
