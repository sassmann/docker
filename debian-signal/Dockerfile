FROM debian:sid
RUN apt-get update \
    && apt-get install -yq --no-install-recommends curl gnupg apt-transport-https ca-certificates \
    && curl -s https://updates.signal.org/desktop/apt/keys.asc | apt-key add - \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN echo "deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main" > /etc/apt/sources.list.d/signal-xenial.list \
    && apt-get update \
    && apt-get install -yq --no-install-recommends libx11-xcb1 libasound2 hunspell libgtk-3-0 libcanberra-gtk3-module packagekit-gtk3-module signal-desktop \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENV PULSE_SERVER unix:/tmp/pulse

CMD ["signal-desktop","--no-sandbox"]
