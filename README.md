## Configuration for Local Development

1. Copy the `example.settings.local.php` file in the **sites** folder to the **sites/default** folder
2. Rename it to `settings.local.php`
3. Open the `settings.php` folder and uncomment the following lines 

```php
# if (file_exists($app_root . '/' . $site_path . '/settings.local.php')) {
#   include $app_root . '/' . $site_path . '/settings.local.php';
# }
```

```php
# $settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';
```

4. Add the following lines to the `development.services.yml`
```yml
parameters:
  http.response.debug_cacheability_headers: true
  twig.config:
    debug: true
    auto_reload: true
    cache: false
services:
  cache.backend.null:
    class: Drupal\Core\Cache\NullBackendFactory
```