# Rendering

Almost every blade file can be overwritten or extended on your resources.

- [Create views](#create-views)
- [Edit views](#edit-views)
- [Index views](#index-views)
- [Show views](#show-views)

---

<a name="create-views"></a>
## Create views

You can either extend the create livewire component used or just the whole blade file (that contains the livewire component).

```php
public $createLivewireComponent = 'rambo-resource-create';
public $createView = 'rambo::livewire.crud.resource-create';

public function createLivewireComponent()
{
    return $this->createLivewireComponent;
}

public function createView()
{
    return $this->createView;
}
```

<a name="edit-views"></a>
## Edit views

You can either extend the edit livewire component used or just the whole blade file (that contains the livewire component).

```php
public $editLivewireComponent = 'rambo-resource-edit';
public $editView = 'rambo::livewire.crud.resource-edit';

public function editLivewireComponent()
{
    return $this->editLivewireComponent;
}

public function editView()
{
    return $this->editView;
}
```

<a name="index-views"></a>
## Index views

You can either extend the index livewire component used or just the whole blade file (that contains the livewire component).

```php
public $indexLivewireComponent = 'rambo-resource-index';
public $indexView = 'rambo::livewire.crud.resource-index';

public function indexLivewireComponent()
{
    return $this->indexLivewireComponent;
}

public function indexView()
{
    return $this->indexView;
}
```

The index table itself can also be extended:

```php
public $indexTableBlade = 'rambo::components.crud.tables.index';
public $preLoadIndex = true;

public function indexTableBlade()
{
    return $this->indexTableBlade;
}
```

<a name="show-views"></a>
## Show views

You can either extend the show livewire component used or just the whole blade file (that contains the livewire component).

```php
public $showLivewireComponent = 'rambo-resource-show';
public $showView = 'rambo::livewire.crud.resource-show';

public function showLivewireComponent()
{
    return $this->showLivewireComponent;
}

public function showView()
{
    return $this->showView;
}
```
