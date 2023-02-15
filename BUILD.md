# Build Docker images

## Build GovCMS D10 PoC images

### Build images

```bash
docker buildx build --push --secret id=github_token,src=./configs/auth.json --platform linux/amd64,linux/arm64 --tag govcmspoc/govcms:10.x-poc --file Dockerfile.govcms .
```

### Build slim images

```bash
docker buildx build --push --secret id=github_token,src=./configs/auth.json --platform linux/amd64,linux/arm64 --tag govcmspoc/govcms:10.x-poc-slim --file .docker/Dockerfile.slim.govcms .
```
