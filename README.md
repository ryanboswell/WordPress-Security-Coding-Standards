# WordPress Security Coding Standards
> A trimmed down ruleset focusing on security coding standards for WordPress.

Adhering to code standards is a very good thing, and the [WordPress Coding Standards](wpcs) are a very important tool in developing any WordPress project whether a plugin, theme, or core contribution. But sometimes the plethora of primarily code style sniffs can really get in the way of using PHPCS on a legacy project and it can be difficult to identify the most important items that should be addressed.

This was born out of a need to quickly evaluate third party plugins for security concerns, while ignoring code style standards. But this ruleset is also a good start for sniffing critical issues in any legacy plugin that hasn't been adhering to the WPCS.

## Prerequisites

1.  PHPCS
2.  WordPress Coding Standards

## Installation

1.  Install prerequisites above.
2.  Clone this repository
```sh
git clone https://github.com/ryanboswell/WordPress-Security-Coding-Standards.git
```
3.  Add its path to PHP_CodeSniffer configuration
```sh
phpcs --config-set installed_paths /path/to/WordPress-Security-Coding-Standards
```

Note, for third step, if you have previously installed standards (like WPCS), you'll need to include those to the `installed_paths` argument like below or they'll be lost. You can view what the current config is with `phpcs --config-show`
```sh
phpcs --config-set installed_paths /path/to/wpcs,/path/to/WordPress-Security-Coding-Standards
```

## Usage

Usage is pretty simple, just point the `--standard` flag of `phpcs` to this standard and run.

```sh
phpcs --standard=WordPress-Security /path/to/wp/project/
```

## Contributing

The work here is definitely not comprehensive, so outside contributions are more than welcome.

1.  Fork the repository.
2.  Create a feature branch on your fork from the `master` branch.
3.  Make and commit your changes (please use descriptive commit messages).
4.  Open a Pull Request to `master` on the original repository and request a review.


[wpcs]: https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards
