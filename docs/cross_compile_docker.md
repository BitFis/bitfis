# Cross compile arm on x86 container with rancher

## Run

```bash
# open rancher
wsl -d rancher-desktop

# install qemu
sudo apk update
sudo apk add qemu qemu-img qemu-system-x86_64

# check version
qemu-system-x86_64 --version

# enable qemu in rancher docker
docker run --rm --privileged multiarch/qemu-user-static --reset -p yes

# test it is working
docker run --rm -t arm64v8/ubuntu uname -m
```

## Cross compile

```bash
# cross compile locally
docker buildx build --platform linux/arm64 -t test .
```

## References:

- https://www.stereolabs.com/docs/docker/building-arm-container-on-x86
