# laravel-simple-thumbnail
Laravel simple thumbnail without gd or imagick requirements


# Laravel Thumbnail

[![Build](https://github.com/elseyyid/laravel-simple-thumbnail/actions/workflows/php.yml/badge.svg)](https://github.com/elseyyid/laravel-simple-thumbnail/actions/workflows/php.yml)
[![PHP Version](https://img.shields.io/packagist/php-v/elseyyid/laravel-simple-thumbnail.svg)](https://github.com/elseyyid/laravel-simple-thumbnail/blob/master/composer.json)
[![Latest Stable Version](https://poser.pugx.org/elseyyid/laravel-simple-thumbnail/v/stable)](https://packagist.org/packages/elseyyid/laravel-simple-thumbnail)
[![LICENSE](https://img.shields.io/packagist/l/elseyyid/laravel-simple-thumbnail.svg)](https://github.com/elseyyid/laravel-simple-thumbnail/blob/master/LICENSE)

![image](docs/assets/img/auth.png) ![image resized](docs/assets/img/auth_resized.png)

```html
<img src="{{ Thumbnail::src(public_path('/img/auth.png'))->format('jpg')->smartcrop(450, 450)->url() }}">
<!-- <img src="/storage/sdf334.jpg?src=auth.png&smartcrop=200x200"> -->
```

Laravel simple package to resize images with specially formatted URLs.

- Generates the URL without touching the filesystem.
- Rendered thumbnails are stored and subsequent requests are directly served from your nginx/apache.
- The URL is signed to prevent malicious parameters.

## Getting Started

### Requirements

- php >= 7.1.3
- laravel >= 5.5

### Installation

To install the most recent version with composer run the following command.

```bash
composer require elseyyid/laravel-simple-thumbnail
```

## Usage

```php
<img src="{{ Thumbnail::src($path)->crop(64, 64)->url() }}" />


<?php
    //load image from dir
    \Thumbnail::src(public_path('images/example.jpeg'));

    //load image from Storage::disk('local')
    \Thumbnail::src('userimage.jpg', 'local' /* disk */);

    //load image from website
    \Thumbnail::src('https://picsum.photos/200');
?>
```

Checkout the [docs](https://elseyyid.github.io/laravel-simple-thumbnail/) for more examples.

## Configuration

Publish the configuration file with the following command.

```bash
php artisan vendor:publish --tag=thumbnail-config
```

The configuration file is located at `config/thumbnail.php`.

## Commands

Deletes the generated thumbnails.

```bash
php artisan thumbnail:purge
```

## Tests

```php
php vendor/bin/phpunit
```

## License

[MIT](LICENSE)
