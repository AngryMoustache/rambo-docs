# Buttons

Information on making buttons can be found in the [Buttons](/{{route}}/{{version}}/resources/buttons) section.

- [Create Buttons](#create-buttons)
- [Edit Buttons](#edit-buttons)

---

<a name="create-buttons"></a>
## Create Buttons

The create buttons are the buttons that will be displayed on the `create` page of a resource.

You can overwrite this method on your resource to add your own buttons.

```php
public function createButtons()
{
    return [
        CancelButton::make(),
        SubmitButton::make(),
    ];
}
```

<a name="eddit-buttons"></a>
## Edit Buttons

The edit buttons are the buttons that will be displayed on the `edit` page of a resource.

You can overwrite this method on your resource to add your own buttons.

```php
public function editButtons()
{
    return [
        CancelButton::make(),
        SubmitContinueButton::make(),
        SubmitButton::make(),
    ];
}
```
