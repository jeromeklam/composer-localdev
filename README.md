# Fork from https://github.com/gossi/composer-localdev-plugin
---

For complete documentation, go to original site.

## Updates

* RelativePath for linux based development.

## Installation

```
$ composer global require 'jeromeklam/composer-localdev'
$ composer global update
```

## Usage

```
{
    "config": {
        "localdev": {
            "": ["/path/to/your/packages"],
            "vendor/package": "/path/to/package",
	    "my/package": "../local-dev/package"
        }
    }
}
```

**Relative path, from composer.json file**
