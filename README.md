# Проект по инфобезу

## Описание проекта
Данное Web-приложение на фреймворке Symfony предназначено для проверки фишинговых писем, которое позволяет сисадминам и обычным пользователям отличать настоящие письма от фишинговых.

## Шаги выполнения кода
1.	Подключение необходимых библиотек через **Composer**.
2.	Извлечение домена из поля **From**.
3.	Получение **SPF-записи** для домена.
4.	Парсинг **SPF-записи** и извлечение диапазонов подсетей.
5.  Извлечение **IP-адреса** отправителя из заголовков **Received**.
6.  Проверка принадлежности **IP-адреса** диапазонам подсетей.

## Установка и запуск
1.	В терминале выполнить команду `docker build -t mail-web .` для сборки контейнера.
2.	В терминале выполнить команду `docker run -d -p 8000:8000 mail-web` для запуска контейнера.
3.  Для доступа к веб-сервису открыть браузер и перейти по следующему адресу: `http://localhost:8000`.

## Пример результата анализа
```
Адрес отправителя: =?utf-8?B?0JLQu9Cw0LTQsCDQkdC+0YDQuNGB0L7QstCw?= <borisova.vvl@dvfu.ru>

Извлеченный домен: dvfu.ru

SPF-запись для домена: v=spf1 include:spf.protection.outlook.com include:mail.dvfu.ru include:protection.outlook.com include:_spf.yandex.net include:spf.unisender.ru -all

IP-адрес отправителя: 2a02:6b8:c0c:11a9:0:640:3025:0 - Соответствует SPF-записи
```

## Бонус
Приложение развёрнуто в Kubernetes, что обеспечивает его масштабируемость и надёжность.

## Репозиторий проекта
Проект доступен на GitHub по [ссылке](https://github.com/kawa11Tensh1/Mail_guard-web.git).