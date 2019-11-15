# Prerequisites
Docker installed on Mac.

This setup is based on https://github.com/docker-library/docs/blob/master/centos/README.md .

# Build the Image
```bash
$ docker build --rm -t local/c7-systemd --file dockerfile.builder .
```

Without the `--file` -option you get an error:
```
failed to solve with frontend dockerfile.v0: failed to read dockerfile:
open /var/lib/docker/tmp/buildkit-mount932003717/Dockerfile: no such file or directory
```

# Use the Image

## Build the Runner Image
```bash
$ docker build --rm -t local/c7-systemd-httpd --file dockerfile.runner .
```

## Run the Runner Image
```bash
$ docker run -ti -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 8880:80 local/c7-systemd-httpd
```
