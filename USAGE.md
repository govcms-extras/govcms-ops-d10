
## Drupal Rector

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