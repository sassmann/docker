FROM ubuntu

RUN echo 'deb [arch=amd64,i386] http://repo.steampowered.com/steam precise steam' > /etc/apt/sources.list.d/steam-inst.list && dpkg --add-architecture i386
RUN apt-get update && apt-get install -yq --no-install-recommends --force-yes sudo alsa-utils libgl1-mesa-dri steam
RUN rm -rf /etc/apt/sources.list.d/steam-inst.list
RUN apt-get update && apt-get install -yq libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libc6:i386 libnss3:i386 dbus:i386

RUN echo 'steam ALL = NOPASSWD: ALL' > /etc/sudoers.d/steam
RUN chmod 0440 /etc/sudoers.d/steam
RUN adduser --disabled-password --gecos 'Steam' steam
RUN ln -s /bin/dbus-daemon /usr/bin/dbus-daemon

ENV ALSA_CARD 0
USER steam
ENV HOME /home/steam
VOLUME /home/steam

CMD sudo /etc/init.d/dbus start && steam
