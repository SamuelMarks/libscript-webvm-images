libscript-webvm-images
----------------------
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache-2.0-yellow.svg)](https://opensource.org/licenses/Apache-2.0)

For details see:

  - https://cheerpx.io/docs/guides/custom-images
  - https://github.com/leaningtech/alpine-image (which this greatly inherits from; and is somewhat a fork)

## Usage

### Image build

    buildah build -f 'alpine.Dockerfile' --dns='none' --platform 'linux/i386' -t 'libscript_webvm_alpine':'latest'

### Image run

    podman create --name 'run_libscript_webvm_alpine' 'libscript_webvm_alpine':'latest'
    mkdir cheerpXFS
    podman unshare podman cp 'run_libscript_webvm_alpine':/ cheerpXFS/
    podman unshare mkfs.ext2 -b 4096 -d cheerpXFS/ cheerpXImage.ext2 600M

### Cleanup

    podman rm 'run_libscript_webvm_alpine'
    buildah rmi 'libscript_webvm_alpine':'latest'
    rm -rf cheerpXFS

---

## License

Licensed under

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or <https://apache.org/licenses/LICENSE-2.0>)

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
licensed as above, without any additional terms or conditions.
