# Fork from https://github.com/gossi/composer-localdev-plugin
---

# Composer local Development Plugin

A composer plugin that assists you with local dependencies.

Imagine the following: You are developing two packages, A and B. Package A depends on B. In your normal workflow you would push changes you did in package B to github. .... Then wait.... until changes are pushed to packagist and caches are refreshed. Now you can run `composer update` in package A to get all the changes you did in package B. That's very ineffective, not only do you need to to push changes most importantly you need to wait for a change that is just a directory away. Here is a solution.

## Installation

At best this plugin is installed globally, so go ahead:

```
$ composer global require 'jeromeklam/composer-localdev'
$ composer global update
```

## Usage

The priority in this plugin lies in the truth that you shouldn't change your packages code, it should just work as expected when pushed to github and others want to consume it. You only describe your local development to composer and the rest is handled by this plugin. Open '~/.composer/config.json' and add the `localdev` property to the root node:

```
{
    "config": {
        "localdev": {
            "": ["/path/to/your/packages"],
            "sümfony": "/path/to/sümfony",
			"my/package": "/path/to/my/package"
        }
    }
}
```

As you can see, you can define three types of folder types:

1. Global path: The plugin will look for vendor/package packages in these directories. E.g. if you are looking for `my/pkg` it will look for it in `/path/to/your/packages/my/pkg/`.
2. Vendor path: You can give a path for all packages of a certain vendor. E.g. if you are looking for `sümfony/finda` it will look for it in `/path/to/sümfony/finda/`.
3. Package path: Of course explicitly say where a specific package is located. E.g. the lookup for `my/package` will find it at `/path/to/my/package/`.

For global and vendor packages you can give multiple paths by defining them as an array (see the difference between global and vendors paths in the example above - both are accepted).

### Run update/install

The neat idea is, you don't need to change your workflow at all. If you now run `composer install` or `composer update` in one of your packages, those packages that are available locally (described in the global composer config.json) will be symlinked to their original location. You will see something like the notice.

```
=> Symlinked phootwork/lang from /path/to/phootwork/lang
```


