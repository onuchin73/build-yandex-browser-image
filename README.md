# Build yandex browser image for selenoid

`$BROWSER_VERSION` = Browser version from [Yandex repository](https://repo.yandex.ru/yandex-browser/deb/pool/main/y/yandex-browser-stable/).  
`$DRIVER_VERSION` = Linux version of the Yandex browser driver from [Yandex repository](https://github.com/yandex/YandexDriver/releases/). 

`$BROWSER_VERSION` format = 1.1.1.1-1
`$DRIVER_VERSION` format = 1.1.1.1

#1 clone this repository : git clone https://github.com/onuchin73/build-yandex-browser-image.git  
#2 go to the folder : cd buildYandexBrowser  
#3 run build by bash : docker build --build-arg BROWSER_VERSION=$BROWSER_VERSION --build-arg DRIVER_VERSION=$DRIVER_VERSION -t MyUSER/yandex_browser:$BROWSER_VERSION .  
