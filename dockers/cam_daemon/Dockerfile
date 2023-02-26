From ubuntu:latest
LABEL maintainer="Sebastien Druon (sebastien.druon@umontpellier.fr)"
ARG cam
ARG module
ARG ip
ENV cam_id "${cam}"
ENV mod_id "${module}"
ENV cam_ip "${ip}"
ENV width "1920"
ENV height "1200"
ENV fps	"30"
RUN apt-get update && \
DEBIAN_FRONTEND=noninteractive TZ=Europe/Paris apt-get install -y \
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
CMD ./sbl_cam_daemon -d 1 -w $width -h $height -f $fps -o /workspace -m $mod_id -c $cam_id $cam_ip
