# PSR 12 with Stroustrup + Spaces coding style

This ruleset for PHPCS and PHPCBF adheres to PSR 12 with three changes:

1. Stroustrup brackets (a K&R variant).
    - The opening bracket is always on the same line
    - No else-cuddling or other compression of control structures, i.e. `else` and `catch` keywords are on their own line (followed by the opening bracket).

2. Spaces in Parentheses
    - One space before and after statement inside parentheses in control structures
    - One space after ! in control structures

3. Space around functions
    - One blank line before and after functions

Inspired by [this question on Stackoverflow](https://stackoverflow.com/questions/62300584/vs-code-php-auto-formatting-beautify-with-stroustrup-style-braces-kr-variant).

## Example

```PHP
<?php

namespace Bar;

class Foo {

  public function baz() {
    if ( ! false ) {
      echo('Hello World!');
    }
    else {
      die();
    }
  }

}

```

## Installation

1. Install [Composer](https://getcomposer.org/).

2. Add the following section to your `composer.json` (perhaps preferrably in the global context). This makes this repository visible for composer (replace the github address with your own if you fork the project). You can locate your `composer.json` with `composer config home` or `composer global config home`.

```json
{
    "repositories": [
        {
            "type": "vcs",
            "url": "git@github.com:nicolajknudsen/psr12-stroustrup-and-space"
        }
    ]
}
```

3. Run the following to install the project and dependencies, including dev dependencies. Add a `global` if you are installing globally. Allow the plugin from "dealerdirect/phpcodesniffer-composer-installer" when prompted.

```bash
composer require nicolajknudsen/psr12-stroustrup-and-space:dev-master
```

That's it. Check that the coding standard is available by running `phpcs -i`.

## VS Code

To make use of the linting and fixing ability af PHPCS and PHPCBF in VS Code, complete the following steps:

1. Install the [PHPSAB extension in VS Code](https://github.com/valeryan/vscode-phpsab).
2. Point the config to `/path/to/composer/vendor/bin`. Follow the guide in the extension documentation, or just open `settings.json` in VS Code with `ctrl+shift+P` and add the following config:

```json
{
  "phpsab.executablePathCS": "/path/to/composer/vendor/bin/phpcs",
  "phpsab.executablePathCBF": "/path/to/composer/vendor/bin/phpcbf",
  "phpsab.standard": "psr12-stroustrup-and-space",
  "phpsab.debug": true,
  "phpsab.fixerEnable": true,
  "phpsab.snifferEnable": true,
  "phpsab.snifferShowSources": true
}

```
