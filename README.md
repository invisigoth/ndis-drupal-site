# NDIS

## Create a .env file in /

~~~~
MYSQL_DATABASE=DATABASE
MYSQL_HOSTNAME=127.0.0.1
MYSQL_PASSWORD=root
MYSQL_PORT=3306
MYSQL_USER=password

# Another common use case is to set Drush's --uri via environment.
DRUSH_OPTIONS_URI=https://your.testing.domain

# Environment mode for theme
NDIS_THEME_MODE=dev
~~~~

## Create a settings.local.php in /web/sites/default
```php
<?php
assert_options(ASSERT_ACTIVE, true);
\Drupal\Component\Assertion\Handle::register();

$settings['trusted_host_patterns'] = [
  '^your\.domain\.com$',
];

```

### If in development mode, settings.local.php should be similar to:
```php
<?php
assert_options(ASSERT_ACTIVE, true);
\Drupal\Component\Assertion\Handle::register();

$settings['container_yamls'][]                     = DRUPAL_ROOT . '/sites/default/local.services.yml';
$config['system.logging']['error_level']           = 'verbose';
$config['system.performance']['css']['preprocess'] = false;
$config['system.performance']['js']['preprocess']  = false;
$settings['cache']['bins']['render']               = 'cache.backend.null';
$settings['cache']['bins']['page']                 = 'cache.backend.null';
$settings['cache']['bins']['dynamic_page_cache']   = 'cache.backend.null';
$settings['skip_permissions_hardening']            = true;
$settings['trusted_host_patterns']                 = [
  '^your\.domain\.com$',
];

```
## Install

* composer install
* cd web/themes/custom/ndis
* npm install
* npm run build/watch
