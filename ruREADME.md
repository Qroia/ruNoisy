# ruNoisy

- Рус версия (вы тут)
- [EN Language](README.md)

Простой скрипт на python, который генерирует случайный шум HTTP/DNS трафика в фоновом режиме, пока вы занимаетесь своим обычным веб-серфингом, чтобы сделать данные вашего веб-трафика менее ценными для продажи и для дополнительной неизвестности.

Проверен на MacOS High Sierra, Ubuntu 16.04 (и PopOS! <= 20.04, 21.10 и 22.04) и Raspbian Stretch и совместим с Python 2.7 и 3.6.

- [ruNoisy](#runoisy)
	- [Что нового в ruNoisy?](#что-нового-в-runoisy)
	- [Начало](#начало)
	- [Зависимости](#зависимости)
	- [Использование](#использование)
	- [Выходные данные](#выходные-данные)
	- [Авторы](#авторы)
	- [Лицензия](#лицензия)
	- [Благодарности](#благодарности)

## Что нового в ruNoisy?

В данный момент, когда вы используете Noisy(неважно, изменён ли конфиг или нет), важно не допустить момента, когда Вы кидаете в оператора "пыль"(Посещения ссылок), а кидаются алмазы("Неправильные" ссылки)

- Новые корневые ссылки
- Синхронизация с RuBlackList

## Начало

Эти инструкции помогут вам создать копию проекта и запустить его на локальной машине

## Зависимости

Установите `requests`, если он у вас еще не установлен, с помощью `pip`:

```
pip install requests
```

## Использование

Скачайте клон репозитория

```
git clone https://github.com/Qroia/ruNoisy.git
```

Перейдите в папку `ruNoisy`

```
cd ruNoisy
```

Запустите скрипт

```
python3 noisy.py --config config.json
```

Программа может принимать ряд аргументов командной строки:

```
$ python3 noisy.py --help
usage: noisy.py [-h] [--log -l] --config -c [--timeout -t]

optional arguments:
  -h, --help    show this help message and exit
  --log -l      logging level
  --config -c   config file
  --timeout -t  for how long the crawler should be running, in seconds
```

требуется только аргумент config-файл.

## Выходные данные

```
$ docker run -it noisy --config config.json --log debug
DEBUG:urllib3.connectionpool:Starting new HTTP connection (1): 4chan.org:80
DEBUG:urllib3.connectionpool:http://4chan.org:80 "GET / HTTP/1.1" 301 None
DEBUG:urllib3.connectionpool:Starting new HTTP connection (1): www.4chan.org:80
DEBUG:urllib3.connectionpool:http://www.4chan.org:80 "GET / HTTP/1.1" 200 None
DEBUG:root:found 92 links
INFO:root:Visiting http://boards.4chan.org/s4s/
DEBUG:urllib3.connectionpool:Starting new HTTP connection (1): boards.4chan.org:80
DEBUG:urllib3.connectionpool:http://boards.4chan.org:80 "GET /s4s/ HTTP/1.1" 200 None
INFO:root:Visiting http://boards.4chan.org/s4s/thread/6850193#p6850345
DEBUG:urllib3.connectionpool:Starting new HTTP connection (1): boards.4chan.org:80
DEBUG:urllib3.connectionpool:http://boards.4chan.org:80 "GET /s4s/thread/6850193 HTTP/1.1" 200 None
INFO:root:Visiting http://boards.4chan.org/o/
DEBUG:urllib3.connectionpool:Starting new HTTP connection (1): boards.4chan.org:80
DEBUG:urllib3.connectionpool:http://boards.4chan.org:80 "GET /o/ HTTP/1.1" 200 None
DEBUG:root:Hit a dead end, moving to the next root URL
DEBUG:urllib3.connectionpool:Starting new HTTPS connection (1): www.reddit.com:443
DEBUG:urllib3.connectionpool:https://www.reddit.com:443 "GET / HTTP/1.1" 200 None
DEBUG:root:found 237 links
INFO:root:Visiting https://www.reddit.com/user/Saditon
DEBUG:urllib3.connectionpool:Starting new HTTPS connection (1): www.reddit.com:443
DEBUG:urllib3.connectionpool:https://www.reddit.com:443 "GET /user/Saditon HTTP/1.1" 200 None
...
```

## Авторы

- **Itay Hury** - _Первоначальная работа_ - [1tayH](https://github.com/1tayH)
- **Qroia** - _ру Форк_ - [Qroia](https://github.com/Qroia)

## Лицензия

Этот проект лицензирован по лицензии GNU GPLv3 - см. [LICENSE.md](LICENSE.md) файл

## Благодарности

Этот проект был вдохновлен

- [RandomNoise](http://www.randomnoise.us)
- [web-traffic-generator](https://github.com/ecapuano/web-traffic-generator)
