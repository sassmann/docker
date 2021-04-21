FROM debian:sid

RUN printf 'path-exclude=/usr/share/locale/*\npath-exclude=/usr/share/doc/*\npath-include=/usr/share/locale/en/*' > /etc/dpkg/dpkg.cfg.d/purge
RUN apt-get update && apt-get install -yq --no-install-recommends \
    firefox libgtk-3-0 libgtk-3-common libcurl4 libnspr4 libnss3 libpango1.0 libcanberra-gtk3-module libxt6 packagekit-gtk3-module libgl1-mesa-dri libvdpau-va-gl1 va-driver-all fonts-dejavu pulseaudio fonts-noto-cjk icedtea-netx-common
    #firefox wget libgtk2.0 libgtk-3-0 libgtk-3-common libcurl4 libnspr4 libnss3 libpango1.0 libcanberra-gtk3-module libxt6 packagekit-gtk3-module libgl1-mesa-dri libvdpau-va-gl1 va-driver-all fonts-dejavu pulseaudio fonts-noto-cjk icedtea-netx-common
#RUN sed -i '0,/RE/s/main/main contrib non-free/' /etc/apt/sources.list
#RUN apt-get update && apt-get install -yq --no-install-recommends libglvnd-dev libglx-nvidia0 mesa-utils libnvidia-egl-wayland-dev strace
RUN mkdir -p /etc/firefox/
RUN /bin/echo -e '\
pref("browser.crashReports.unsubmittedCheck.autoSubmit", true);\n\
pref("browser.startup.homepage","data:text/plain,browser.startup.homepage=https://www.startpage.com");\n\
pref("datareporting.healthreport.service.firstRun", false);\n\
pref("datareporting.healthreport.uploadEnabled", false);\n\
pref("datareporting.policy.dataSubmissionPolicyBypassNotification", true);\n\
pref("reader.parse-on-load.enabled", false);\n\
pref("signon.rememberSignons", false);\n\
pref("media.ffmpeg.vaapi.enabled", true);\n\
pref("layers.acceleration.force-enabled", true);\n\
pref("toolkit.telemetry.reportingpolicy.firstRun", false);\n'\
>> /etc/firefox/syspref.js
#FIXME: does not stick
#pref("browser.search.widget.inNavBar", true);\n\

RUN adduser --disabled-password user --gecos "User"
USER user
RUN mkdir /home/user/.cache
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

CMD ["firefox","--new-instance","about:blank"]
