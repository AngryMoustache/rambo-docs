# Rambo helper object

Rambo comes with a helper Facade called `RamboBreadcrumbs`.
With it, you can manipulate the breadcrumbs in the CMS.

Below is a list of available methods, in alphabetical order.

- [RamboBreadcrumbs::list()](#list)
- [RamboBreadcrumbs::reset()](#reset)
- [RamboBreadcrumbs::add($label, $link = null)](#add)

---

<a name="add"></a>
## RamboBreadcrumbs::add($label, $link = null)

Adds a new link at the end of the breadcrumbs.

If a link is not given, it will be set to the current URL.

<a name="list"></a>
## RamboBreadcrumbs::list()

Returns the current breadcrumbs in a collection.

<a name="reset"></a>
## RamboBreadcrumbs::reset()

Resets the breadcrumbs to an empty collection.
