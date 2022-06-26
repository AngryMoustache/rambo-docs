# The Resource object

Rambo uses Resources to display its data in the CRUD.

This page will go over some basics, but more detailed information can be found under the [Resource Traits](/{{route}}/{{version}}/traits/actions) section.

---

## Creating a new resource

You'll need a folder to put your Resources in, usually this is called `app/Rambo`.

A bare-bones resource will look like this, for example a resource for the `Page` model:

```php
<?php

namespace App\Rambo;

use AngryMoustache\Rambo\Resource;

class Page extends Resource
{
    public function fields()
    {
        return [
            //
        ];
    }
}
```

Notice the `fields()` method, this is the only method you are required to have, here we define the fields that the resource will display, more information about fields can be found under the [Fields](/{{route}}/{{version}}/fields) section.

## Resource constructor

The constructor of the resource will take care of some things like the label etc.
However you can define these yourself as well, see more under the [Resource Traits](/{{route}}/{{version}}/traits/actions) section.

```php
public function __construct()
{
    $name = Str::afterLast(get_class($this), '\\');
    $label = Str::ucfirst(implode(' ', preg_split('/(?=[A-Z])/', $name)));

    $this->singularLabel ??= trim(Str::afterLast($label, '\\'));
    $this->label ??= trim(Str::plural($this->singularLabel));
    $this->routebase ??= Str::kebab($this->label);
    $this->model ??= 'App\\Models\\' . $name;
}
```

## Sorting and pagination

You can define a default way of sorting and the amount of pagination your resource on relation and index queries, see the [Sorting](/{{route}}/{{version}}/digging-deeper/queries) section for more information about Rambo queries.

```php
public $defaultOrderCol = 'id';
public $defaultOrderDir = 'desc';
public $pagination = 25;

public function defaultOrderCol()
{
    return $this->defaultOrderCol;
}

public function defaultOrderDir()
{
    return $this->defaultOrderDir;
}

public function pagination()
{
    return $this->paginate ?? $this->pagination;
}
```
