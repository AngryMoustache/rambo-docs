# Permissions

You can redefine the permissions for your resources by overwriting the many permission methods.

- [Default Permission](#default-permission)
- [Can View Index](#can-view-index)
- [Can Edit](#can-edit)
- [Can Show](#can-show)
- [Can Create](#can-create)
- [Can Delete](#can-delete)

---

<a name="default-permission"></a>
## Default permission

The resource has a simple default permissions boolean, when set to `false` you won't be able to do anything with the resource, as every other permission function will use this as its fallback.

```php
public $defaultPermission = true;

public function getDefaultPermission()
{
    return $this->defaultPermission;
}
```

<a name="can-view-index"></a>
## Can View Index

Will determine wether the user can view the index of the resource.

```php
public function canViewIndex()
{
    return $this->getDefaultPermission();
}
```

<a name="can-edit"></a>
## Can Edit

Will determine wether the user can edit the resource.

```php
public function canEdit()
{
    return $this->getDefaultPermission();
}
```

<a name="can-show"></a>
## Can Show

Will determine wether the user can view the resource detail page.

```php
public function canShow()
{
    return $this->getDefaultPermission();
}
```

<a name="can-create"></a>
## Can Create

Will determine wether the user can create a resource model.

```php
public function canCreate()
{
    return $this->getDefaultPermission();
}
```

<a name="can-delete"></a>
## Can Delete

Will determine wether the user can delete the resource.

```php
public function canDelete()
{
    return $this->getDefaultPermission();
}
```
