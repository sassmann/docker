FROM debian:unstable
SHELL ["/bin/bash", "-c"]

RUN sed -i '0,/RE/s/main/main contrib/' /etc/apt/sources.list
RUN printf 'path-exclude=/usr/share/locale/*\npath-exclude=/usr/share/doc/*\npath-include=/usr/share/locale/en/*' > /etc/dpkg/dpkg.cfg.d/purge
RUN apt-get update && apt-get install -yq --no-install-recommends \
    firefox flashplugin-nonfree libgl1-mesa-dri libvdpau-va-gl1 va-driver-all fonts-dejavu pulseaudio \
    && update-flashplugin-nonfree --install \
    && mv /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/mozilla/plugins/ \
    && apt-get autoremove -y flashplugin-nonfree \
    && rm -rf /tmp/* /var/{tmp,cache}/* /var/lib/{apt,dpkg}/

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

CMD ["firefox","--new-instance","about:blank"]
