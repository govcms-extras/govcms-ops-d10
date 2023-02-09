
## Drupal Rector

https://github.com/palantirnet/drupal-rector

Analyze your code with Rector and review suggested changes.

```bash
ahoy rector process web/modules/minisite --dry-run
```

Apply suggested changes

```bash
ahoy rector process web/modules/minisite
```

## PHPUnit

```bash
ahoy phpunit -c web/core web/modules/minisite
```

## Drupal Check

https://github.com/mglaman/drupal-check

```bash
ahoy drupal-check web/modules/minisite
```
