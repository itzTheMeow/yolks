FROM        --platform=$TARGETOS/$TARGETARCH node:18-bullseye-slim

LABEL       author="Meow" maintainer="me@itsmeow.cat"

RUN         apt update \
            && apt -y install ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev python3-pip ca-certificates dnsutils tzdata zip tar curl build-essential libtool \
            && python3 -m pip install -U yt-dlp \
			&& useradd -m -d /home/container container

RUN         npm install npm@latest pnpm@latest -g

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
