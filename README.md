Composer Package Repository
===


![deploy status](../..//actions/workflows/main.yml/badge.svg)


Powered by [satis](https://github.com/composer/satis).


### Usage

Add this repository to your project's `composer.json`. Ex:

```
composer config repositories.astral composer https://packages.company.com/
```


### Configuration

[documentation for `satis.json`](https://getcomposer.org/doc/articles/handling-private-packages.md#setup)


#### Add Package

Edit `satis.json`, add your package under `repositories`.

`vendor-name/module-name` must be the same as defined in the package's `composer.json`.

```json
{
    "repositories": [
        {
            "name": "vendor-name/module-name",
            "type": "vcs",
            "url": "https://github.com/VendorName/Module-Name.git"
        }
    ]
}
```

SSH url can also be used for repository url (eg `git@github.com:VendorName/Module-Name.git`).

#### Providing Authentication For Protected Packages

If you have included private/protected packages, you should provide authentication:

```
composer config github-oauth.github.com <your-github-token>
```


### Trigger Rebuild

When any of the included packages have been updated, you may trigger a partial rebuild to update te repository.

[documentation for partial rebuild](https://getcomposer.org/doc/articles/handling-private-packages.md#partial-updates)

```
composer satis:build ./satis.json build/ vendor-name/module-name
```
You may provide multiple packages, or omit to rebuild all packages.

Rebuilding takes time, it is highly advised to use partial rebuild:
