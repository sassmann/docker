FROM debian
RUN sed -i '0,/RE/s/main/main contrib/' /etc/apt/sources.list
RUN apt-get update && apt-get install -yq vim-tiny iceweasel flashplugin-nonfree xpdf
RUN apt-get clean
RUN update-flashplugin-nonfree --install

RUN adduser --disabled-password firefox
USER firefox
ENV HOME /home/firefox

CMD ["firefox"]
