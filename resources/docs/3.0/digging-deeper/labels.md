# Labels

You can define labels/primary keys for your resources by using the following methods:

- [Display Name](#display-name)
- [Primary Key](#primary-key)
- [Labels](#labels)

---

<a name="display-name"></a>
## Display Name

Resources will be displayed in your CMS with their ID, unless you define a different display name on your resource.

```php
public $displayName = 'id';

public function displayNameField()
{
    return $this->displayName;
}
```

<a name="primary-key"></a>
## Primary Key

If you are using a different column then `id` for your primary key, you can redefine it on your resource as well.

```php
public $primaryField = 'id';

public function primaryField()
{
    return $this->primaryField;
}
```

<a name="labels"></a>
## Labels

When reading labels in the frontend of the CMS, there are a couple of ways to define them on your resource.

```php
public $label;
public $singularLabel;

public function label()
{
    return $this->label;
}

public function singularLabel()
{
    return $this->singularLabel;
}

public function itemName()
{
    return $this->item->{$this->displayNameField()};
}

public function itemId()
{
    return $this->item->{$this->primaryField()};
}
```

If you want, you can also redefine the label used in the global search component:

```php
public function globalSearchLabel()
{
    return $this->label();
}
```
