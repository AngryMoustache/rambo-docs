# Buttons

Buttons are used to add actions on the edit or create CRUD pages.

The standard buttons that come with any Rambo CRUD page are:

## Cancel Button

Returns to the previous page.

## Submit Button

Save and and return to the specified page (usually the index.)

## Submit Continue Button

Save and stay on the current page.

---

## Creating a custom button

You could create a custom button, all you need to define is a label and action.

```php
<?php

namespace AngryMoustache\Rambo\Buttons;

class CancelButton extends Button
{
    public $label = 'Cancel';
    public $action = 'cancel';
    public $inline = true;
}
```

The action is a livewire action, so you'll need to extend the Resource livewire components, see the [CRUD components](/{{route}}/{{version}}/crud/components) on how to do this.
