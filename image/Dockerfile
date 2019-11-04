FROM ubuntu:16.04

RUN apt-get update && apt-get clean && apt-get install -y \
    python3-pip \
    bzip2 \
    libgconf-2-4 \
    libgtk2.0-0 \
    dbus-x11 \
    x11vnc \
    xvfb \
    fluxbox \
    wmctrl \
    wget \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list \
    && apt-get update && apt-get -y install google-chrome-stable

RUN useradd apps \
    && mkdir -p /home/apps \
    && chown -v -R apps:apps /home/apps

COPY libgcrypt11_1.5.3-2.deb /

RUN dpkg -i libgcrypt11_1.5.3-2.deb

RUN pip3 install tldextract
RUN pip3 install flask
RUN pip3 install flask_restful
RUN pip3 install configparser

COPY bootstrap.sh /

CMD '/bootstrap.sh'
