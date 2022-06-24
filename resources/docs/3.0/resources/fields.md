# Fields

When creating a resource, you'll need to define fields.
For a list of fields, see the [Fields](/{{route}}/{{version}}/resources/rambo-fields) section.

- [Creating a field](#creating-field)
- [Label](#label)
- [Searchable](#searchable)
- [Sortable](#sortable)
- [Hiding fields](#hiding-fields)
- [Validation](#validation)
- [Defaults](#defaults)
- [Custom component](#custom-component)
- [Specific variables](#specific-variables)

---

<a name="creating-field"></a>
## Creating a field

When making a field, you should be aware that the first argument you pass in the `::make()` function is _always_ the field name in the database. This value will be used when saving your data, for example:

```php
AttachmentField::make('image_id')
```

<a name="label"></a>
## Label

If you want your label in the CMS to be prettier, you can call the `->label($label)` method.

```php
AttachmentField::make('image_id')
    ->label('Image')
```

<a name="searchable"></a>
## Searchable

If you want a field to be searchable in the Index view and in the Global Search, you can add `->searchable()` to your field.

If the field you are using is a custom one, make sure it includes or extends a `search()` function, for example, this is the default one (on the base Field class):

```php
public function search($query, $item = null)
{
    return Str::contains(
        strtolower(($item ?? $this->item)->{$this->getName()}),
        strtolower($query)
    );
}
```

<a name="sortable"></a>
## Sortable

If you want your column to be sortable, you can add `->sortable()` to the field.

```php
TextField::make('title')
    ->sortable()
```

<a name="hiding-fields"></a>
## Hiding fields

You can hide you fields from certain views using `->hideFrom([])`.

```php
TextField::make('title')
    ->hideFrom(['index', 'show', 'edit', 'create'])
```
<a name="validation"></a>
## Validation

You can also pass along rules, just like you would anywhere else in Laravel:

```php
TextField::make('title')
    ->rules('required_if:fields.contact_info,true')
```

```php
TextField::make('amount')
    ->rules(['required_if:fields.contact_info,true', 'number'])
```

<a name="defaults"></a>
## Default values

You can define a default value for your field by calling the `default` method.

```php
TextField::make('name')
    ->default('Clark Kent')
```

<a name="custom-component"></a>
## Custom blade components

There are a couple of blade components that you can overwrite by passing it to your field with the corresponding name, for example `->bladeFormComponent('component-name')`.

First, there are the blade components for the fields, `public $bladeShowComponent` and `public $bladeFormComponent`, these are the blade files that are used when displaying your field anywhere.

Secondly, you could define `public $livewireShowComponent` and `public $livewireFormComponent`, these are used to define a livewire field. By default these are `null`, and when filled will take precedent over the normal blade file.

Lastly, you have the `public indexWrapperComponent` and `public $showWrapperComponent`, you can overwrite these if you wish to have full control over the way your field is shown, including labels, errors etc.

<a name="specific-variables"></a>
## Specific blade variables

Should you, for whatever reason, require a specific variable for a field, you can pass along anything you like.

```php
TextField::make('name')
    ->superman('Clark Kent')
```

You can then call this data in the blade file that hass access to the `$field` variable:

```php
{{ $field->superman }}
```
