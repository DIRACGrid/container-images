# Container images for DiracX

> **Note:** As of diracx v0.0.12, diracx ships its own pixi-based
> runtime image (see `containers/Dockerfile` in the diracx repo).
> The `base`, `services-base`, and `client-base` images previously
> built here are no longer used and are not built by CI.
> Only `secret-generation` is maintained in this repository.

This repository contains the recipes and CI for building the container images used by DiracX.

## Available images

### secret-generation

This image is used by the [helm chart](https://github.com/DIRACGrid/diracx-charts) to run batch jobs within the cluster that automatically generate kubernetes secrets.

## How to build

The most up to date documentation on how to build is the [CI job](.github/workflows/main.yml)

```bash
docker build -t ghcr.io/diracgrid/diracx/secret-generation:latest secret-generation/
```
