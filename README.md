# Build yandex browser image for selenoid

BROWSER_VERSION = Версия браузера из репозиротия яндекса https://repo.yandex.ru/yandex-browser/deb/pool/main/y/yandex-browser-stable/
DRIVER_VERSION = Linux версия драйвера для яндекс браузера из репозиротия яндекса https://github.com/yandex/YandexDriver/releases

docker build --build-arg BROWSER_VERSION=$BROWSER_VERSION --build-arg DRIVER_VERSION=$DRIVER_VERSION -t sqaadmin/yandex_browser:$BROWSER_VERSION .
