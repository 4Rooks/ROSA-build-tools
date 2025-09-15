# ROSA Build Tools
[![Container Registry](https://img.shields.io/badge/container-ghcr.io%2F4rooks%2Frosa--build--tools-blue)](https://github.com/4rooks/rosa-build-tools/pkgs/container/rosa-build-tools)

The **rosa-build-tools** repository provides containerized build environments for the **ROSA** product.
It is designed to make builds reproducible, portable, and isolated across different development setups.

## 📦 Repository Contents

* **Container definitions** (Containerfiles and configuration files) for reproducible ROSA builds.
* **Pre-built container images** published via GitHub Container Registry:

  * `ghcr.io/4rooks/rosa-build-tools:build-env-zephyr-latest`
  * `ghcr.io/4rooks/rosa-build-tools:build-env-zephyr-v4.1.0` *(example pinned release)*

## 🛠️ Usage

### Prerequisites

* [Docker](https://docs.docker.com/get-docker/) or a compatible container runtime (e.g. Podman).
* Git installed on your system.

### Use a pre-built container (recommended)

Pull the latest Zephyr build container:

```bash
docker pull ghcr.io/4rooks/rosa-build-tools:build-env-zephyr-latest
```

Run with the latest container:

```bash
docker run --rm -it --user $(id -u) -v $(pwd):/workspace ghcr.io/4rooks/rosa-build-tools:zephyr-latest
```

Or pin to a specific version (recommended for reproducibility):

```bash
docker pull ghcr.io/4rooks/rosa-build-tools:build-env-zephyr-v4.1.0

docker run --rm -it --user $(id -u) -v $(pwd):/workspace ghcr.io/4rooks/rosa-build-tools:build-env-zephyr-v4.1.0
```

### Build the container locally (optional)

```bash
git clone https://github.com/4rooks/rosa-build-tools.git
cd rosa-build-tools

docker build -f Containerfile.build-env-zephyr -t rosa-build-env-zephyr ./zephyr
docker run --rm -it --user $(id -u) -v $(pwd):/workspace rosa-build-env-zephyr
```
