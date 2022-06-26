# Queries

When displaying resources in the CMS, certain custom queries are being called, you an redefine all of them on your resource.

Below is an alphabetical list of all the queries that are being called on your resources:

- [fetch($id)](#fetch)
- [globalSearchQuery()](#global-search-query)
- [indexQuery()](#index-query)
- [query()](#query)
- [relationQuery()](#relation-query)
- [sortedQuery()](#sorted-query)

---

<a name="fetch"></a>
## fetch($id)

The fetch query will find the model with the given id and attach it to the current resource.

```php
public function fetch($id)
{
    $this->item = $this->query()->find($id);

    return $this;
}
```

<a name="global-search-query"></a>
## globalSearchQuery()

This query will be called to get a list of items to filter on in the global search.

```php
public function globalSearchQuery()
{
    return $this->sortedQuery();
}
```

<a name="index-query"></a>
## indexQuery()

This query will be called to get a list of items to show on the index page.

This query will also be sorted by the [sortedQuery()](#sorted-query) method.s

```php
public function indexQuery()
{
    return $this->query();
}
```

<a name="query"></a>
## query()

This is the default query method that all other queries will start from.

```php
public function query()
{
    return $this->model()::withoutGlobalScopes();
}
```

<a name="relation-query"></a>
## relationQuery()

This is the query that will run when calling the resource via a relation field like HABTM or a Belongs To etc.

```php
public function relationQuery()
{
    return $this->sortedQuery();
}
```

<a name="sorted-query"></a>
## sortedQuery()

This query will sort the results by the default order column and direction.

```php
public function sortedQuery()
{
    return $this->indexQuery()->orderBy(
        $this->defaultOrderCol(),
        $this->defaultOrderDir(),
    );
}
```
