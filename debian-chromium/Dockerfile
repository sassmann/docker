FROM debian

RUN sed -i '0,/RE/s/main/main contrib non-free/' /etc/apt/sources.list
RUN apt-get update && apt-get install -yq --no-install-recommends \
    chromium libgl1-mesa-dri libcanberra-gtk-module libexif-dev pepperflashplugin-nonfree pulseaudio \
    && apt-get clean

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

CMD ["chromium"]
