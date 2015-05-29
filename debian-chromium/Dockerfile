FROM debian

RUN sed -i '0,/RE/s/main/main contrib non-free/' /etc/apt/sources.list
RUN apt-get update && apt-get install -yq --no-install-recommends chromium libcanberra-gtk-module libexif-dev pepperflashplugin-nonfree
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/*

RUN adduser --disabled-password --gecos "User" user
USER user
ENV HOME /home/user

CMD ["chromium"]
