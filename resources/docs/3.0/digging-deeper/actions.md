# Actions

There are a couple ways that you can attach actions to a resource.

Information on making actions can be found in the [Actions](/{{route}}/{{version}}/resources/actions) section.

- [Item Actions](#item-actions)
- [Overview Actions](#overview-actions)
- [Specific Type Actions](#specific-type-actions)
- [Custom Type Actions](#custom-type-actions)

---

<a name="item-actions"></a>
## Item Actions

Item actions are the actions that will be displayed on the `edit` and `show` pages of a resource, and on the `table` as icon actions.

By default actions will refrain from showing themselves on pages that they take you to.

You can overwrite this method on your resource to add your own actions.

```php
public function itemActions()
{
    return [
        ShowAction::make(),
        EditAction::make(),
        DeleteAction::make(),
    ];
}
```

<a name="overview-actions"></a>
## Overview Actions

Overview actions are the actions that will be displayed on the `create` and `index` pages of a resource.

By default actions will refrain from showing themselves on pages that they take you to.

You can overwrite this method on your resource to add your own actions.

```php
public function overviewActions()
{
    return [
        OverviewAction::make(),
        CreateAction::make(),
    ];
}
```

<a name="specific-type-actions"></a>
## Specific Type Actions

You can define actions for specific types of pages, by default they will call the corresponding parent actions.

You can overwrite these methods on your resource to customize your actions.

```php
public function tableActions()
{
    return $this->itemActions();
}

public function showActions()
{
    return $this->itemActions();
}

public function editActions()
{
    return $this->itemActions();
}
```

```php
public function createActions()
{
    return $this->overviewActions();
}

public function indexActions()
{
    return $this->overviewActions();
}
```

<a name="custom-type-actions"></a>
## Custom Type Actions

If you have a completely custom page you can define actions for it and fetch them by calling `->actions('xxx')` on your resource.

```php
public function customTypeActions()
{
    return [
        CustomAction::make(),
    ];
}
```

```php
$this->resource->actions('customType');
// OR
$this->resource->customTypeActions();
```
