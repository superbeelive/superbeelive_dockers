From ubuntu:latest
LABEL maintainer="Sebastien Druon (sebastien.druon@umontpellier.fr)"
RUN apt-get update && \
DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt-get install -y \
	libaravis-dev \
	libaravis-0.8 \
	aravis-tools-cli\
	libusb-1.0 \
	libusb-dev \
	libglib2.0 \
	libglib2.0-dev \
	make \
	gcc \
	binutils \
	autoconf \
	automake \
	libtool \
	pkg-config \
	git \
	file \
	patch \
&& rm -fr /var/lib/apt/lists/*
WORKDIR /root
RUN git clone https://github.com/superbeelive/superbeelive.git
WORKDIR /root/superbeelive/sbl_cam_daemon
RUN make
CMD ["./sbl_cam_daemon", \
	 "-d", "1", \
	 "-w", "1280", "-h", "720", "-f", "30", \
	 "-o", "/workspace", \
	 "-m", "1", "-c", "1", \
	 "192.168.2.3"]
