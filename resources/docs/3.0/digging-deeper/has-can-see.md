# Has Can See

This trait is added on multiple classes in Rambo, it is used for simple permissions.

Permissions for resources can be found in the [Permissions](/{{route}}/{{version}}/digging-deeper/permissions) section.

- [Can Be Seen](#can-be-seen)
- [Should Hide](#should-hide)

---

<a name="can-be-seen"></a>
## Can Be Seen

This method is used to determine if a user can see a certain button/action/...

```php
public function shouldHide($resource)
{
    return false;
}
```

<a name="should-hide"></a>
## Should Hide

This method is used to determine if a user can see a certain button/action/...

```php
public $canSee = true;

public function canBeSeen($resource)
{
    return $this->canSee && ! $this->shouldHide($resource);
}
```
