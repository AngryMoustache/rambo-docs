# Rambo Fields

Rambo comes with pre-defined fields in its package:

- [Attachment Field](#attachment-field)
- [Boolean Field](#boolean-field)
- [Date Time Field](#date-time-field)
- [Editor Field](#editor-field)
- [HABTM Field](#habtm-field)
- [Has Many Field](#has-many-field)
- [ID Field](#id-field)
- [Many Attachment Field](#many-attachment-field)
- [Password Field](#password-field)
- [Select/Belongs To Field](#select-field)
- [Slug Field](#slug-field)
- [Text Field](#text-field)

---

<a name="attachment-field"></a>
## Attachment Field

This field will use the angry-moustache/media package and create a useful modal to select, upload and crop attachments.

```php
\AngryMoustache\Rambo\Fields\AttachmentField::make('image_id'),
```

You can define the folder that you want it to be saved using the `->folder($folder)` method. This "folder" is only used in the index page of the attachments resource. The folder uses dot notation for parent/child "directories".

```php
\AngryMoustache\Rambo\Fields\AttachmentField::make('image_id')
    ->folder('uploads.avatars'),
```

<a name="boolean-field"></a>
## Boolean Field

A simple boolean field.

```php
\AngryMoustache\Rambo\Fields\BooleanField::make('online'),
```

<a name="date-time-field"></a>
## Date Time Field

A simple date-time field, you can define the format used to display the date by passing `->format($format)` to the field.

You can also change the format used on the form by passing `->formFormat($formFormat)` to the field.

```php
\AngryMoustache\Rambo\Fields\DateTimeField::make('online'),
```

<a name="editor-field"></a>
## Editor Field

A WYSIWYG (TipTap) field, can be used to add/edit HTML content.

```php
\AngryMoustache\Rambo\Fields\EditorField::make('description'),
```

<a name="habtm-field"></a>
## HABTM Field

A field that represents a HABTM relation.
The first parameter in this field is the relation name.
You always need to pass a resource, to tell the field what you are relating with.

```php
\AngryMoustache\Rambo\Fields\HabtmField::make('tags')
    ->resource(\App\Rambo\Tag::class),
```

It is possible to have resources be displayed differently by giving the resource a `public $habtmComponent = 'component-name'` property.

<a name="has-many-field"></a>
## Has Many Field

A field that represents a Has Many relation.
The first parameter in this field is the relation name.
You always need to pass a resource, to tell the field what you are relating with.

```php
\AngryMoustache\Rambo\Fields\HasMany::make('tags')
    ->resource(\App\Rambo\Tag::class),
```

This field will be hidden on index, create and edit pages.

<a name="id-field"></a>
## ID Field

The ID field is a simple text field that is used to display the ID of the resource.

```php
\AngryMoustache\Rambo\Fields\IDField::make(),
```

You can pass a different ID key to the field using the `->name($key)` method, should you not be using `id` as your primary key.

<a name="many-attachment-field"></a>
## Many Attachment Field

You can add and sort multiple attachments in this field. It uses the same methods that you can use on the `AttachmentField`. The first parameter in this field is the relation name that stores the attachments.

```php
\AngryMoustache\Rambo\Fields\ManyAttachmentField::make('images'),
```

<a name="password-field"></a>
## Password Field

A password field, if left empty, nothing will be saved/overwritten.

```php
\AngryMoustache\Rambo\Fields\PasswordField::make('password'),
```

<a name="select-field"></a>
## Select/Belongs To Field

A select dropdown, can either pass the options using the `->options($options)` method:

```php
\AngryMoustache\Rambo\Fields\SelectField::make('amount')
    ->options([
        0 => 'zero',
        5 => 'five',
        10 => 'ten',
    ]),
```

Or you can pass a resource class to the field, and the field will automatically generate the options from the resource.

```php
\AngryMoustache\Rambo\Fields\SelectField::make('amount')
    ->resource(Tag::class),
```

<a name="slug-field"></a>
## Slug Field

A text field that will automatically slug the given field, for example the following SlugField will be filled by looking at the `title` field:

```php
\AngryMoustache\Rambo\Fields\SlugField::make('slug')
    ->nameField('title'),
```

If no name field is given, the slug field will be filled by looking at the `name` field.

<a name="text-field"></a>
## Text Field

A simple text field, can't get any more basic than this.

```php
\AngryMoustache\Rambo\Fields\TextField::make('title'),
```
