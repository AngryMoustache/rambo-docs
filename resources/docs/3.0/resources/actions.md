# Actions

Every Resource can linked with actions, these are the actions that will be available in the CRUD.

For information on how to attach actions to a Resource, see the [Resource Traits](/{{route}}/{{version}}/traits/actions) section.

---

## Creating a new action

Making an action is simple enough, let's look at the default `ShowAction` as an example of a "link action":

```php
<?php

namespace AngryMoustache\Rambo\Actions;

use AngryMoustache\Rambo\Facades\Rambo;

class ShowAction extends Action
{
    public $icon = 'far fa-eye';
    public $label = 'Show';

    public function getLink($resource, $item)
    {
        return $resource->show($item->id);
    }

    public function shouldHide($resource)
    {
        return ! $this->resource->canShow()
            || Rambo::currentUrl() === $this->resource->show();
    }
}
```

Notice the `$icon` and `$label` variables, it is important that you give an icon to your action, as this will be used to show the action in your index table.

The label is used when displaying the action on a button, at the top of your CRUD.

Since our action simply returns the URL of the show page, we can use the `getLink()` method to return the URL of the show page.

In order to prevent the show action from showing up on the show page, we can use the `shouldHide()` method to determine if the action should be shown.

## Actions with more complex logic

A more complex action is one that has more than just a link, for example the `DeleteAction`.

```php
<?php

namespace AngryMoustache\Rambo\Actions;

class DeleteAction extends Action
{
    public $icon = 'far fa-trash-alt';
    public $label = 'Delete';

    public $livewireComponent = 'rambo-action-delete';

    public function shouldHide($resource)
    {
        return ! $this->resource->canDelete();
    }
}
```

Here we pass a `$livewireComponent` to the action, this will render the given livewire component in the CRUD.

The Livewire object will be passed the current `$resource`, the action object `$action` and a boolean `$label` to determine wether or not the label is being shown.
