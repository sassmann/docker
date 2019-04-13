FROM i386/ubuntu:18.04

RUN apt update \
    && apt install -y software-properties-common \
    && apt clean
RUN apt dist-upgrade -y \
    && apt install -y sudo pciutils file pulseaudio ca-certificates python3 locales \
    && apt install -y steam vulkan-utils mesa-vulkan-drivers \
    && apt clean \
    && locale-gen en_US.UTF-8

RUN echo 'steam ALL = NOPASSWD: ALL' > /etc/sudoers.d/steam
RUN chmod 0440 /etc/sudoers.d/steam
RUN adduser --disabled-password steam --gecos "Steam"

USER steam
ENV HOME /home/steam
ENV PULSE_SERVER unix:/tmp/pulse

CMD sudo /etc/init.d/dbus start && LIBGL_DEBUG=verbose /usr/games/steam
