# GovCMS D10 development

## Getting started

### Build the project

```bash
git clone git@github.com:govCMS/govcms-ops-d10.git
cd govcms-ops-d10
cp configs/auth.json.example configs/auth.json
vi auth.json # Replace with the Github PAT.
ahoy build
ahoy up
```

Then you can visit http://localhost:8888/

### Fast preview

```bash
docker run --name govcms-d10-test -p 8080:80 -d govcmspoc/govcms:drupal10
```

More examples can be found in USAGE.md
