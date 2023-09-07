FROM archlinux:base-devel

COPY rootfs/ /

RUN pacman -Syu bc dtc cpio arm-none-eabi-gcc \
    		aarch64-linux-gnu-gcc zip python3 \
		inetutils git android-tools --needed --noconfirm && \
		yes | pacman -Scc

RUN mkdir -p /kernel/source && \
    mkdir -p /kernel/toolchain/{clang,gcc}

ENV ARGS="--img"
ENV PATH=/kernel/toolchain/gcc/bin:/kernel/toolchain/clang/bin:$PATH

WORKDIR /kernel/source
CMD bash ./scripts/build ${ARGS}
