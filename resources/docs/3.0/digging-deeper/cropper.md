# Cropper

Rambo comes with a cropper installed, using [Cropper.js](https://fengyuanchen.github.io/cropperjs/).

- [Enabling the cropper](#enabling-the-cropper)
- [Defining Formats](#defining-formats)

---

<a name="enabling-the-cropper"></a>
## Enabling the cropper

The cropper will be on by default, if you wish to disable it, add the following to your `config/media.php` config file:

```php
'cropper' => false,
```

<a name="defining-formats"></a>
## Defining formats

The media library uses the [Spatie Image library](https://spatie.be/docs/laravel-medialibrary/v10/introduction), you'll first need to create a format in the `App\Formats` folder, for example:

```php
<?php

namespace App\Formats;

use AngryMoustache\Media\Formats\Format;
use Spatie\Image\Image;
use Spatie\Image\Manipulations;

class Video extends Format
{
    public static function render(Image $image)
    {
        return $image->crop(Manipulations::CROP_CENTER, 960, 540);
    }
}
```

If you have any specific options that you wish to pass to the cropper for this format, you can add the `cropperOptions` method to the format class.

```php
public static function cropperOptions()
{
    return [
        'aspectRatio' => 1.78,
    ];
}
```

When you are finished making your format, you can add it to the `formats` array in the `config/media.php` config file:

```php
return [
    'cropper' => [
        'formats' => [
            \AngryMoustache\Media\Formats\Thumb::class => 'Thumb',
            \App\Formats\Video::class => 'Video Preview',
        ],
    ],
];
```
