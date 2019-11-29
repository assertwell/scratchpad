# Docker Container

## Concept

A Docker Container (or Docker Compose configuration) designed to test WordPress themes and plugins, especially under different combinations and/or configurations.

### Examples

This might be used to test a single WordPress plugin across multiple versions of WordPress + PHP:

```yaml
env:
  - PHP_VERSION=7.4 WP_VERSION=5.3
  - PHP_VERSION=7.0 WP_VERSION=4.9
```

It may also be used to test certain combinations of plugins:

```yaml
env:
  - WP_PLUGINS=jetpack@latest,woocommerce@3.7
```

## Implementation

[WordPress 5.3 introduced the WordPress Local Environment](https://make.wordpress.org/core/2019/08/05/wordpress-local-environment/), [a series of semi-official Docker containers](https://hub.docker.com/u/wordpressdevelop) made to test WordPress core across different versions of PHP.

We can extend these containers (which use Docker Compose) to build environments that, for example, pre-load test data, install + activate plugins, and more.

Better yet, we can make it possible for developers to run specific combinations locally rather than relying that everything go through docker.

Ideally, this would be handled through a script that will set up the necessary environment, along the lines of:

```sh
$ setup-wp-environment --php=7.3 --wp=trunk --plugin=jetpack --plugin=caldera-forms
$ phpunit
```
