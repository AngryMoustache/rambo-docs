# Routing

Resources routes can be changed, though not recommended.

You can also change the path you take when creating/editing a resource

- [Routebase](#routebase)
- [Route redirects](#route-redirects)
- [Default routes](#default-routes)

---

<a name="routebase"></a>
## Routebase

The routebase of a resource is the slug that is used in the CMS.

It is also the key used when the Rambo helper searches for a resource, see the [Rambo helper](/{{route}}/{{version}}/helpers/rambo) for more information.

```php
public $routebase;

public function routebase()
{
    return $this->routebase;
}
```

<a name="route-redirects"></a>
## Route redirects

You can change the behaviour of the create and edit components by setting certain redirect methods on your resource.

By default they redirect to the show page of your resource.

```php
public function routeAfterCreate()
{
    return $this->show();
}

public function routeAfterEdit()
{
    return $this->show();
}
```

<a name="default-routes"></a>
## Default routes

These are the default routes that Rambo will use, while possible, it is not recommended to extend these routes.

These methods can be called where-ever you have a resource in your code (Controller/Livewire/blade/etc.)

```php
public function index()
{
    return route('rambo.crud.index', $this->routebase());
}

public function create()
{
    return route('rambo.crud.create', $this->routebase());
}

public function show($id = null)
{
    return route('rambo.crud.show', [
        'resource' => $this->routebase(),
        'itemId' => $id ?? $this->itemId(),
    ]);
}

public function edit($id = null)
{
    return route('rambo.crud.edit', [
        'resource' => $this->routebase(),
        'itemId' => $id ?? $this->itemId(),
    ]);
}
```
