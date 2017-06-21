FROM debian:unstable
SHELL ["/bin/bash", "-c"]

#RUN sed -i '0,/RE/s/main/main contrib/' /etc/apt/sources.list
RUN printf 'path-exclude=/usr/share/locale/*\npath-exclude=/usr/share/doc/*\npath-include=/usr/share/locale/en/*' > /etc/dpkg/dpkg.cfg.d/purge
RUN apt-get update && apt-get install -yq --no-install-recommends \
    firefox wget libcurl3 libnspr4 libnss3 libpango1.0 libcanberra-gtk3-module packagekit-gtk3-module libgl1-mesa-dri libvdpau-va-gl1 va-driver-all fonts-dejavu pulseaudio \
    && wget http://www.deb-multimedia.org/pool/non-free/f/flash-player/flashplayer-mozilla_26.0.0.126-dmo1_amd64.deb \
    && dpkg -i flashplayer-mozilla_26.0.0.126-dmo1_amd64.deb \
    && rm -rf /tmp/* /var/{tmp,cache}/* /var/lib/{apt,dpkg}/

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

CMD ["firefox","--new-instance","about:blank"]
