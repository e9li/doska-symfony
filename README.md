# Doska for Symfony

Dev-only Symfony toolbar. Point at an element, write a note, and copy a prompt that names the controller, the Twig file and line, and the Symfony UX component. A connected agent can also read and resolve notes through the stateless MCP endpoint.

The bundle does nothing unless `kernel.debug` is true. Register it for the `dev` and `test` environments only.

## Install

```bash
composer require --dev doska/symfony
```

```php
// config/bundles.php
Doska\DoskaBundle::class => ['dev' => true, 'test' => true],
```

```yaml
# config/routes/doska.yaml
when@dev:
    doska:
        resource: '@DoskaBundle/config/routes.php'
```

If the app firewall starts a session for every URL, exclude `/_doska` the same way as `/_profiler` and `/_wdt`. The routes are stateless.

Clear the cache once so Twig recompiles with the source map:

```bash
php bin/console cache:clear
```

See the [canonical Doska README](https://git.e9li.com/e9li/doska) for the prompt contents, configuration, accessibility checks, notes panel, and agent setup. Development happens in that monorepo; this package repository is generated and is read-only.

## License

MIT
