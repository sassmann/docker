FROM debian:sid
RUN dpkg --add-architecture i386 \
    && apt-get update \
    && apt-get install -yq --no-install-recommends libpulse0 pulseaudio wget curl \
    && curl http://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb > /usr/src/skype.deb \
    && dpkg --force-depends -i /usr/src/skype.deb \
    && apt-get install -fy \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

CMD ["skype"]
