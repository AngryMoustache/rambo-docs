# Configuration

Rambo comes with a config file that you can/should publish, below is an alphabetical list of all the options that are available.

- [admin-guard](#admin-guard)
- [admin-route](#admin-route)
- [cropper](#cropper)
- [navigation](#navigation)
- [resources](#resources)

---

<a name="admin-guard"></a>
## admin-guard

When using a custom guard for logging in, you can define it here.

```php
'admin-guard' => 'rambo',
```

<a name="admin-route"></a>
## admin-route

If you wish to use another route prefix for your CMS routes, you can change it here.

```php
'admin-route' => 'admin',
```

<a name="cropper"></a>
## cropper

When using the cropper, you'll need to add new formats in the `config/media.php` config file.

If no formats are defined, the cropper will not be available.

```php
'cropper' => [
    'formats' => [
        \AngryMoustache\Media\Formats\Thumb::class => 'Thumb',
    ],
],
```

<a name="navigation"></a>
## navigation

You'll need to define the navigation here, you can define folders by using a key with the value being an array of resource classes.

Make sure you define the used resources in the `resources` config (see below), or the navigation will throw an error.

```php
'navigation' => [
    Administrator::class,
    'Media' => [
        Attachment::class,
    ],
],
```

<a name="resources"></a>
## resources

When making new resources, you'll need to tell Rambo they exist, you can do this by adding it in the config.

```php
'resources' => [
    Attachment::class,
    Administrator::class,
],
```
