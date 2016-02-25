# laravel-failed-job-monitor

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/laravel-failed-job-monitor.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-failed-job-monitor)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/spatie/laravel-failed-job-monitor/master.svg?style=flat-square)](https://travis-ci.org/spatie/laravel-failed-job-monitor)
[![SensioLabsInsight](https://img.shields.io/sensiolabs/i/f2aaa07e-2960-4ed5-a130-626e990fef3f.svg?style=flat-square)](https://insight.sensiolabs.com/projects/f2aaa07e-2960-4ed5-a130-626e990fef3f)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/laravel-failed-job-monitor.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/laravel-failed-job-monitor)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/laravel-failed-job-monitor.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-failed-job-monitor)

This package sends notifications if a queued job fails. Services for sending notifications can be specified in the config file.

Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## Install

You can install the package via composer:
``` bash
$ composer require spatie/laravel-failed-job-monitor
```

Next up, the service provider must be registered:

```php
'providers' => [
    ...
    Spatie\FailedJobMonitor\FailedJobMonitorServiceProvider::class,

];
```

Next, you must publish the config file:

```bash
php artisan vendor:publish --provider="Spatie\FailedJobMonitor\FailedJobMonitorServiceProvider"
```

You must change the published config file and add your own info.
The services like mail or slack (the one you want to use here) must be configured.

For mailing you can use Laravel Mailer.
If you would like to find out how to configure and start using the Mailer follow this link: https://laravel.com/docs/5.2/mail#sending-mail

If you want to use slack for this notifications, you must install 'maknz/slack' package.
You can find this package and the documentation about it on [github] (https://github.com/maknz/slack) or on [packagist](https://packagist.org/packages/maknz/slack).

This is the content of the configuration file, that must be updated:
```php
return [

        /**
         *
         * The services that are wanted to be used to receive the notifications when a queued job fails
         * must be specified in the senders array.
         * More services can be added.
         *
         **/

        'senders' => ['mail', 'slack'],

        //these are mail notifications configurations
        'mail' => [
            'from' => 'your@email.com',
            'to' => 'your@email.com',
        ],

        //these are slack notifications configurations
        'slack' => [
            'channel' => '#failed-jobs',
            'username' => 'Failed Job Bot',
            'icon' => ':robot_face:',
        ],

        // if needed more services can be added here

];

```

## Usage

Once the configurations are added to the config file and there is a failing job you will receive a notification via your chosen senders.


## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Credits

- [Jolita Grazyte](https://github.com/JolitaGrazyte)
- [All Contributors](../../contributors)

## About Spatie
Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
