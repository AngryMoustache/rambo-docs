# Rambo helper object

Rambo comes with a helper Facade called `Rambo`.
With it, you can fetch certain variables used across your CMS.

Below is a list of available methods, in alphabetical order.

- [Rambo::cropperEnabled()](#cropperEnabled)
- [Rambo::currentUrl()](#currentUrl)
- [Rambo::login($email, $password)](#login)
- [Rambo::logout()](#logout)
- [Rambo::navigation()](#navigation)
- [Rambo::notFound()](#notFound)
- [Rambo::passwordHash($password)](#passwordHash)
- [Rambo::resource($value, $id = null, $key = null)](#resource)
- [Rambo::resources()](#resources)
- [Rambo::serving()](#serving)
- [Rambo::unauthorized()](#unauthorized)
- [Rambo::user()](#user)

---

<a name="cropperEnabled"></a>
## Rambo::cropperEnabled()

Checks and returns wether or not the cropper has been enabled for the media library.

<a name="currentUrl"></a>
## Rambo::currentUrl()

Fetch the current Rambo URL.

<a name="login"></a>
## Rambo::login($email, $password)

Attempt to login with an administrator using the given credentials.

<a name="logout"></a>
## Rambo::logout()

Log the current administrator out.

<a name="navigation"></a>
## Rambo::navigation()

Fetch the navigation menu in a collection, defined in the `config/rambo.php` file.

<a name="notFound"></a>
## Rambo::notFound()

Throws a Rambo specific 404 error.

<a name="passwordHash"></a>
## Rambo::passwordHash($password)

Hashes the given string for Rambo login.

<a name="resource"></a>
## Rambo::resource($value, $id = null, $key = null)

Returns a Rambo resource object, the `$value` should be the `routebase` used by the resource.
If given an ID it will populate the resource with that object.
If trying to finds a resource using a field other than `routebase`, pas the preferred field name as the `$key` parameter.

<a name="resources"></a>
## Rambo::resources()

Returns a collection of Rambo resource objects, defined in the `config/rambo.php` file.

<a name="serving"></a>
## Rambo::serving()

Check if the current page is a Rambo page.
It performs this check by checking if the `RamboAuthMiddleware` middleware is loaded on the current route.

<a name="unauthorized"></a>
## Rambo::unauthorized()

Throws a Rambo specific 403 error.

<a name="user"></a>
## Rambo::user()

Returns the current user/administrator.
