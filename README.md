# WordPress Security Coding Standards
> A trimmed down ruleset focusing on security coding standards for WordPress.

Adhering to code standards is a very good thing, and the [WordPress Coding Standards][wpcs] are a very important tool in developing any WordPress project whether a plugin, theme, or core contribution. But sometimes the plethora of primarily code style sniffs can really get in the way of using PHPCS on a legacy project and it can be difficult to identify the most important items that should be addressed.

This was born out of a need to quickly evaluate third party plugins for security concerns, while ignoring code style standards. But this ruleset is also a good start for sniffing critical issues in any legacy plugin that hasn't been adhering to the WPCS.

## The Base Rules

The code sniffs I've included and the severity elevation I've done on some of them (from warning to error) are focused on a more enterprise-security minded environment. These are the base rules I used to decide what sniffs to include and what not to.

1.  **File system reads and writes are disallowed.** This is important in multi-server installations where accessing the filesystem (outside of `wp-content/uploads`) is considered highly un-reliable and un-safe.
2.  **No PHP runtime changes.** In production environments, it's generally unwise to change runtime configuration on the fly, so don't do it.
3.  **Minimize dead or debug code.** This is mostly a code style, but can also be a major security check. If vast portions of code are commented out, that could be a security hole and it warrants further investigation.
4.  **Some things don't work in a cached environment.** When running a WordPress site behind a caching layer, it's important to know what information is safe to use and set and what is not. Cookies and session data can get cached if you're not careful and expose sensitive data to other users. So it's best not to mess with those.
5.  **Validate and Sanitize All The Things.** Should be self-explanatory.

## Prerequisites

1.  [PHPCS][phpcs]
2.  [WordPress Coding Standards][wpcs]

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
[phpcs]: https://github.com/squizlabs/PHP_CodeSniffer
