FROM debian:sid

RUN apt-get update && apt-get install -yq --no-install-recommends \
	python-pip \
	python-dev \
	python-setuptools

RUN pip install wheel
RUN pip install vobject parsedatetime gcalcli
RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user

ENTRYPOINT ["gcalcli"]
