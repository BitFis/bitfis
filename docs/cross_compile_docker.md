# Cross compile arm on x86 container with rancher

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

## References:

- https://www.stereolabs.com/docs/docker/building-arm-container-on-x86
