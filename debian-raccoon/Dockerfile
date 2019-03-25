FROM debian:sid
SHELL ["/bin/bash", "-c"]

RUN printf 'path-exclude=/usr/share/locale/*\npath-exclude=/usr/share/doc/*\npath-include=/usr/share/locale/en/*' > /etc/dpkg/dpkg.cfg.d/purge
RUN apt-get update && apt-get install -yq wget default-jre xfonts-scalable \
    && rm -rf /tmp/* /var/{tmp,cache}/* /var/lib/{apt,dpkg}/

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

RUN cd ; wget http://raccoon.onyxbits.de/sites/raccoon.onyxbits.de/files/raccoon-4.5.0.jar

CMD ["java","-jar","/home/user/raccoon-4.5.0.jar"]
