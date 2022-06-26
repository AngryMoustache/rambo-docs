# Global Search

The global search is a tool that allows you to search across all of your resources at once.

- [Custom blade components](#custom-blade-components)
- [Disabling resources](#disabling-resources)
- [Paginated resources](#paginated-resources)
- [Searching resources](#searching-resources)
- [Weigh resources](#weigh-resources)

---

<a name="custom-blade-components"></a>
## Custom blade components

Should you feel the need to create a custom blade file for the result of a specific resource (for example adding an image or counter), you can do so by editing the `globalSearchBladeComponent` property or extending the `globalSearchBladeComponent()` method on your resource.

```php
public $globalSearchBladeComponent = 'rambo::components.global-search.item';

public function globalSearchBladeComponent()
{
    return $this->globalSearchBladeComponent;
}
```

<a name="disabling-resources"></a>
## Disabling resources

If you want to disable a specific resource from the global search, you can do so by editing the `isGlobalSearchable` property or extending the `isGlobalSearchable()` method on your resource.

```php

```php
public $isGlobalSearchable = true;

public function isGlobalSearchable()
{
    return $this->isGlobalSearchable;
}
```

<a name="paginated-resources"></a>
## Paginated resources

You can change the amount of items shown in the global search by editing the `globalSearchPagination` property or extending the `globalSearchPagination()` method on your resource.

```php
public $globalSearchPagination = 10;

public function globalSearchPagination()
{
    return $this->globalSearchPagination;
}
```

<a name="searching-resources"></a>
## Searching resources

The global search will search across all fields on your resources that have `->searchable()` set to `true`.

You can either overwrite the `search` method or you can extend the `search` method on your fields.

```php
public function search($query, $item = null)
{
    $searchableFields = $this->searchableFields();
    foreach ($searchableFields as $field) {
        if ($field->search($query, $item ?? $this->item)) {
            return true;
        }
    }
    return false;
}
```

<a name="weigh-resources"></a>
## Weigh resources

If you want a certain resource to be more important than others, you can do so by editing the `globalSearchWeight` property or extending the `globalSearchWeight()` method on your resource.

The higher the weight, the more important it will be treated as.

```php
public $globalSearchWeight = null;

public function globalSearchWeight()
{
    return $this->globalSearchWeight;
}
```
