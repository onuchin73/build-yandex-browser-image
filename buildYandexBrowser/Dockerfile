FROM browsers/base:7.4.1

ARG BROWSER_VERSION=1.1.1.1-1
ARG DRIVER_VERSION=1.1.1.1

LABEL browser=yandex-browser-stable:$BROWSER_VERSION

RUN \
        apt-get update && \
        apt-get -y --no-install-recommends install gconf-service \
         libasound2 \
         libatk1.0-0 \
         libc6 \
         libcairo2 \
         libcups2 \
         libdbus-1-3 \
         libexpat1 \
         libfontconfig1 \
         libfreetype6 \
         libgcc1 \
         libgconf-2-4 \
         libgdk-pixbuf2.0-0 \
         libglib2.0-0 \
         libgtk2.0-0 \
         libgtk-3-0 \
         libnspr4 \
         libnss3 \
         libnotify4 \
         libpango1.0-0 \
         libstdc++6 \
         libx11-6 \
         libx11-xcb1 \
         libxcb1 \
         libxcomposite1 \
         libxcursor1 \
         libxdamage1 \
         libxext6 \
         libxfixes3 \
         libxi6 \
         libxrandr2 \
         libxrender1 \
         libxss1 \
         libxtst6 \
         debconf \
         gnupg \
         libudev1 \
         ca-certificates \
         fonts-liberation \
         libappindicator3-1 \
         libnss3 \
         lsb-base \
         xdg-utils \
         binutils \
         jq \
         libgbm1 \
         wget \
         libcurl4 \
         curl && \
         rm -Rf /tmp/* && \
         rm -Rf /var/lib/apt/lists/*

RUN  \
	curl -L -O \$(curl -s https://api.github.com/repos/yandex/YandexDriver/releases \
		| grep browser_download_url \
		| grep yandexdriver-$DRIVER_VERSION-linux.zip \
		| cut -d '"' -f 4) && \
        unzip -o yandexdriver-$DRIVER_VERSION-linux.zip -d ./ && \
        rm -f yandexdriver-$DRIVER_VERSION-linux.zip
        
RUN  \
	curl -s https://repo.yandex.ru/yandex-browser/YANDEX-BROWSER-KEY.GPG | apt-key add - && \
	echo 'deb [arch=amd64] https://repo.yandex.ru/yandex-browser/deb stable main' > /etc/apt/sources.list.d/yandex-browser.list && \
	apt-get update && \
	apt-get -y --no-install-recommends install yandex-browser-stable=$BROWSER_VERSION && \
	yandex-browser --version && \
	rm /etc/apt/sources.list.d/yandex-browser.list && \
	rm -Rf /tmp/* && rm -Rf /var/lib/apt/lists/*

COPY yandexdriver /usr/bin/
COPY entrypoint.sh /

RUN chmod +x /usr/bin/yandexdriver
RUN chmod +x /entrypoint.sh

USER selenium

EXPOSE 4444
ENTRYPOINT ["/entrypoint.sh"]
