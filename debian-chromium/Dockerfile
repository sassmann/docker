FROM debian

RUN sed -i '0,/RE/s/main/main contrib non-free/' /etc/apt/sources.list
RUN apt-get update && apt-get install -yq --no-install-recommends chromium libgl1-mesa-dri libcanberra-gtk-module libexif-dev pepperflashplugin-nonfree pulseaudio
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/*

RUN adduser --disabled-password --gecos "User" user
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse
CMD ["chromium"]
