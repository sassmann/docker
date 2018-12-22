FROM ubuntu:18.04

# data only container for steam

ENV user steam
ENV data /home/steam

# set user and group
RUN groupadd $user && useradd -s /bin/false -g $user $user
# create directory and set permissions
RUN mkdir -p $data && chown -R $user:$user $data

USER steam
# create .drirc
RUN echo "<driconf></driconf>" > /home/$user/.drirc

VOLUME $data
