![Laravel Wallet](./images/yos-laravel-telegram-log.svg)

<div style="text-align: center;">

[![Laravel Unit Test](https://github.com/Yemeni-Open-Source/laravel-telegram-log/actions/workflows/laravel-unit-test.yml/badge.svg)](https://github.com/Yemeni-Open-Source/laravel-telegram-log/actions/workflows/laravel-unit-test.yml)
![Packagist Downloads](https://img.shields.io/packagist/dt/Yemeni-Open-Source/laravel-telegram-log?color=blue&label=Downloads&logo=packagist&logoColor=white)
![Packagist Version](https://img.shields.io/packagist/v/Yemeni-Open-Source/laravel-telegram-log?color=green&label=Version&logo=laravel&logoColor=white)
![GitHub](https://img.shields.io/github/license/Yemeni-Open-Source/laravel-telegram-log?logo=Open%20Source%20Initiative&label=License&logoColor=white&color=blueviolet)

</div>

# Laravel Telegram log

Laravel telegram log is a package that can catch your logs all quite simply.

## Requirments

This package is tested with Laravel v8 it my not work on Laravel v7 or v6 or v5

|||
|-|-|
|php| ^7.3&#124;^8.0|
|Composer| ^2.3|
|Laravel| ^8.0|

## Installation

Install the package by using composer:

> ```composer require yemeni-open-source/laravel-telegram-log```

## Configure Your Needs

You can scape this step if you want to use default configuration, but you can publish telegram logs configuration by running:

> ```php artisan vendor:publish --provider="YemeniOpenSource\TelegramLog\TelegramLogServiceProvider" --tag=config```

This will merge the ```config/telegramlog.php``` config file to your root ```config``` directory. You are free to modify it.

## Setup

### Create Telegram bot

Create new telegram bot as following steps:

- visit [@BotFather](https://telegram.me/BotFather)
- send ```/newbot``` to the [@BotFather](https://telegram.me/BotFather) chat.
- replay with the name of your new bot.
- then replay with the username for your bot.
- copy your bot **token**.

### Open New Chat with your created bot

- visit [t.me/username_of_your_bot](http://t.me/username_of_your_bot)
- send ```Hi``` or any text message.
- visit [https://api.telegram.org/bot<**YourBOTToken**>/getUpdates](https://api.telegram.org/bot<YourBOTToken>/getUpdates)
- copy your **```id```** which inside ```chat``` object.

### Update your .env file

```env
LOG_CHANNEL=telegram
TELEGRAM_LOGGER_BOT_TOKEN=<your-bot-api-token>
TELEGRAM_LOGGER_CHAT_ID=<your-bot-chat-id>
```

### Add Telegram Log Channel

- Add the ```telegram``` logging channel to your ```config/logging.php```.

```php
'channels' => [
    // ...
    'telegram' => [
        'driver' => 'custom',
        'via' => YemeniOpenSource\TelegramLog\Services\TelegramService::class,
        'level' => 'debug',
    ],
    // ...
],
```

## Credits

The MIT License (MIT). Please see [MIT license](LICENSE) File for more information.
