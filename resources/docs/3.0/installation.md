# Installation

## Requirements

You'll need Laravel 9+ and php version 8.1+ to use Rambo v3.0.

## Setup

First install the packages:

```bash
composer require angry-moustache/rambo
```

Then you'll want to publish the required assets, you can also publish the views and config file, but those are not required.

```bash
php artisan vendor:publish --tag=rambo-required-assets
php artisan vendor:publish --tag=rambo-config
```

After that run laravel migration to get the rambo specific tables and seed an administrator

```bash
php artisan migrate --seed
```

You can now log in on the `/admin` route, using the test user!

Username: admin

Password: test
