FROM debian
RUN sed -i '0,/RE/s/main/main contrib/' /etc/apt/sources.list
RUN apt-get update && apt-get install -yq --no-install-recommends iceweasel flashplugin-nonfree libgl1-mesa-dri libvdpau-va-gl1 va-driver-all fonts-dejavu pulseaudio
RUN apt-get clean
RUN update-flashplugin-nonfree --install
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/*

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse
CMD ["firefox"]
