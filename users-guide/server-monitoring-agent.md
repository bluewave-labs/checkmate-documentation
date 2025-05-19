---
icon: eyes
---

# Server monitoring agent

To collect hardware information from your servers, you need Capture, a server monitoring agent for Checkmate. Capture receives requests from Checkmate (server), and sends necessary infrastructure status data.

Capture is a hardware monitoring agent that collects hardware information from the host machine and exposes it through a RESTful API. The agent is designed to be lightweight and easy to use.

## Features

- CPU Monitoring
  - CPU Temperature
  - CPU Load
  - CPU Frequency
  - CPU Usage
- Memory Monitoring
- Disk Monitoring
  - Usage
  - Inode Usage
  - Read/Write Bytes
- S.M.A.R.T. (System Monitoring and Reporting Tool) monitoring

> **Warning:** S.M.A.R.T. monitoring is only available when using binary installation (not Docker). It also requires the `smartmontools` package to be installed on your system, as Capture relies on the `smartctl` utility for collecting S.M.A.R.T. data. Install `smartmontools` using your system's package manager (e.g., `apt install smartmontools` for Debian/Ubuntu, `yum install smartmontools` for CentOS/RHEL).

## Docker Installation

Docker installation is **recommended** for running the Capture. Please see the [Docker run flags](#docker-run-flags) section for more information.

Pull the image from the registry and then run it with one command.

```shell
docker run -v /etc/os-release:/etc/os-release:ro \
    -p 59232:59232 \
    -e API_SECRET=REPLACE_WITH_YOUR_SECRET \
    -d \
    ghcr.io/bluewave-labs/capture:latest
```

If you don't want to pull the image, you can build and run it locally.

```shell
docker buildx build -f Dockerfile -t capture .
```

```shell
docker run -v /etc/os-release:/etc/os-release:ro \
    -p 59232:59232 \
    -e API_SECRET=REPLACE_WITH_YOUR_SECRET \
    -d \
    capture:latest
```

### Docker run flags

Before running the container, please make sure to replace the `REPLACE_WITH_YOUR_SECRET` with your own secret.

! **You need to put this secret to Checkmate's infrastructure monitoring dashboard**

- `-v /etc/os-release:/etc/os-release:ro` to get platform information correctly
- `-p 59232:59232` to expose the port 59232
- `-d` to run the container in detached mode
- `-e API_SECRET=REPLACE_WITH_YOUR_SECRET` to set the API secret
- (optional) `-e GIN_MODE=release/debug` to switch between release and debug mode

```shell
docker run -v /etc/os-release:/etc/os-release:ro \
    -p 59232:59232 \
    -e API_SECRET=REPLACE_WITH_YOUR_SECRET \
    -d \
    ghcr.io/bluewave-labs/capture:latest
```

## System Installation

### Pre-built Binaries

You can download the pre-built binaries from the [GitHub Releases](https://github.com/bluewave-labs/capture/releases) page.

Recommended installation path is `/usr/local/bin`.

Do not forget to make the binary executable.

```shell
chmod +x /usr/local/bin/capture
```

### Go Package

You can install the Capture using the `go install` command.

```shell
go install github.com/bluewave-labs/capture/cmd/capture@latest
```

### Build from Source

You can build the Capture from the source code.

#### Prerequisites

- [Git](https://git-scm.com/downloads) is essential for cloning the repository.
- [Go](https://go.dev/dl/) is required to build the project.
- [Just](https://github.com/casey/just/releases) is optional but **recommended** for building the project with pre-defined commands.

#### Steps

1. Clone the repository

   ```shell
   git clone git@github.com:bluewave-labs/capture
   ```

2. Change the directory

   ```shell
   cd capture
   ```

3. Build the Capture

   ```shell
   just build
   ```

   or

   ```shell
   go build -o dist/capture ./cmd/capture/
   ```

4. Run the Capture

   ```shell
   ./dist/capture
   ```

## Environment Variables

Configure the capture with the following environment variables:

| Variable     | Description                          | Required/Optional | Type      | Default Value                         | Accepted Values  |
| ------------ | ------------------------------------ | ----------------- | --------- | ------------------------------------- | ---------------- |
| `API_SECRET` | The secret key for the API           | Required          | `string`  | -                                     | Any string value |
| `PORT`       | The port that the Capture listens on | Optional          | `integer` | 59232                                 | 0 - 65535        |
| `GIN_MODE`   | The mode of the Gin framework        | Optional          | `string`  | system -> debug <br>docker -> release | release, debug   |

### Example

Please make sure to replace the default `your_secret` with your own secret.

! **You need to put this secret to Checkmate's infrastructure monitoring dashboard**

```shell
PORT = your_port
API_SECRET = your_secret
GIN_MODE = release/debug
```

```shell
# API_SECRET is required
API_SECRET=your_secret GIN_MODE=release ./capture

# Minimal required configuration
API_SECRET=your_secret ./dist/capture
```
