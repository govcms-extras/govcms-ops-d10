## Docker images

Build GovCMS D10 PoC images

```bash
docker buildx build --platform linux/amd64,linux/arm64 --tag govcmspoc/govcms:10.x-poc --file Dockerfile.govcms .
```
