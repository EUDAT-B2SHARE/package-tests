FROM node:latest

# Based on instructions at https://github.com/segmentio/nightmare/issues/224

RUN apt-get update && \
    apt-get install -y \
            xvfb \
            x11-xkb-utils \
            xfonts-100dpi \
            xfonts-75dpi \
            xfonts-scalable \
            xfonts-cyrillic \
            x11-apps \
            clang \
            libdbus-1-dev \
            libgtk2.0-dev \
            libnotify-dev \
            libgnome-keyring-dev \
            libgconf2-dev \
            libasound2-dev \
            libcap-dev \
            libcups2-dev \
            libxtst-dev \
            libxss1 \
            libnss3-dev \
            gcc-multilib \
            g++-multilib

COPY entrypoint.sh /entrypoint
RUN chmod +x /entrypoint

WORKDIR /workspace
ADD package.json /workspace
RUN npm install

ADD . /workspace

ENTRYPOINT ["/entrypoint"]
CMD ["npm", "test"]

#ENV DEBUG="nightmare"