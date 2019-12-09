<!-- Main Header  -->
<div align='center'>

<img src="./assets/theia.svg" width="125px">

## Theia Applications - Docker & Electron

[![Build Status](https://travis-ci.org/theia-ide/theia-apps.svg?branch=master)](https://travis-ci.org/theia-ide/theia-apps)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-curved)](https://github.com/theia-ide/theia-apps/labels/help%20wanted)
[![Questions](https://img.shields.io/badge/Questions-blue.svg?style=flat-curved)](https://github.com/theia-ide/theia-apps/issues?utf8=%E2%9C%93&q=label%3Aquestion+)

Collection of example cloud & desktop applications built using the [Theia](https://github.com/eclipse-theia/theia) platform.

</div>

---

<br />

### Outline

- [Docker Image Variants](#docker-image-variants)
- [Additional Docker Examples](#additional-docker-examples)
- [Electron Applications](#electron-apps)
- [Running & Debugging](#running-&-debugging)
- [Tips & Tricks](#tips-&-tricks)
    - [Build Options](#build-options)
- [Contributing](#contributing)
- [License](#license)

<br />

### Docker Image Variants

<img
    src='./assets/docker.png'
    alt='docker logo'
    width="125px"
/>

| Image Name | Description | Documentation |
|:---|:---|:---|
| [theiaide/theia-cpp](https://hub.docker.com/r/theiaide/theia-cpp) | Theia-based C/C++ example application | [docs](./theia-cpp-docker/README.md) |
| [theiaide/theia-dart](https://hub.docker.com/r/theiaide/theia-dart) | Theia-based Dart example application | |
| [theiaide/theia-full](https://hub.docker.com/r/theiaide/theia-full) | Theia-based example application with all available published applications | |
| [theiaide/theia-go](https://hub.docker.com/r/theiaide/theia-go) | Theia-based Go example application | [docs](./theia-go-docker/README.md) |
| [theiaide/theia-java](https://hub.docker.com/r/theiaide/theia-java) | Theia-based Java example application | |
| [theiaide/theia-python](https://hub.docker.com/r/theiaide/theia-python) | Theia-based Python example application | [docs](./theia-python-docker/README.md) |
| [theiaide/theia-ruby](https://hub.docker.com/r/theiaide/theia-ruby) | Theia-based Ruby example application | |
| [theiaide/theia-rust](https://hub.docker.com/r/theiaide/theia-rust) | Theia-based Rust example application | [docs](./theia-rust-docker/README.md) |
| [theiaide/theia-swift](https://hub.docker.com/r/theiaide/theia-swift) | Theia-based Swift example application | |
| [theiaide/theia](https://hub.docker.com/r/theiaide/theia) | Theia-based JavaScript/TypeScript (Web Technologies) example application | |
| [theiaide/yangster](https://hub.docker.com/r/theiaide/yangster) | Theia-based JavaScript/TypeScript (Web Technologies) example application | |

---

<br />

### Additional Docker Examples

| Image Name | Description | Documentation |
|:---|:---|:---|
| `theia-deb-build-docker` | Example on how to package the IDE into a Debian package | [docs](./theia-deb-build-docker/README.md) |
| `theia-https-docker` | Example on how to add security layer over existing images | [docs](./theia-https-docker/README.md) |
| `theia-openshift-docker` | Example image for OpenShift | |
| `theia-rpm-build-docker` | Example on how to package the IDE into an RPM | [docs](./theia-rpm-build-docker/README.md) |

<br />

### Electron Apps

<img
    src='./assets/electron.png'
    alt='electron logo'
    width="50px"
/>

| Application Name | Description | Documentation |
|:---|:---|:---|
| `theia-cpp-electron` | Theia-based C/C++ desktop IDE | [docs](./theia-cpp-electron/README.md) |
| `theia-electron` | Theia-based JavaScript/TypeScript (Web Technologies) desktop IDE | [docs](./theia-electron/README.md) |

---

<br />

### Running & Debugging

[![dockeri.co](http://dockeri.co/image/theiaide/theia)](https://hub.docker.com/r/theiaide/theia/)

`theiaide/theia` image contains an example of Theia based IDE for Web Developers.

At the moment Theia is still in [active development](https://github.com/theia-ide/theia#roadmap). It is recommended to use [`theiaide/theia:next`](#typefoxtheianext) image to have a look at the current state.

This script pulls the image and runs Theia IDE on http://localhost:3000 with the current directory as a workspace. The option of `--init` is added to fix the [defunct process problem](https://github.com/theia-ide/theia-apps/issues/195).

#### Running

```
# Linux or macOS
docker run -it --init -p 3000:3000 -v "$(pwd):/home/project:cached" theiaide/theia:next

# Windows
docker run -it --init -p 3000:3000 -v "%cd%:/home/project:cached" theiaide/theia:next
```

#### Debugging

You can pass additional arguments after the image name, for example to enable debugging:

```
# Linux or macOS
docker run -it --init -p 3000:3000 --expose 9229 -p 9229:9229 -v "$(pwd):/home/project:cached" theiaide/theia:next --inspect=0.0.0.0:9229
    
# Windows
docker run -it --init -p 3000:3000 --expose 9229 -p 9229:9229 -v "%cd%:/home/project:cached" theiaide/theia:next --inspect=0.0.0.0:9229
```

<br />

## Tips & Tricks

- #### Build Options:
    - `--build-arg strip=true` strips the application to save space but with reduced debuggability.
    - `--init` injects an instance of [tini](https://github.com/krallin/tini) in the container, that will wait-for and reap terminated processes, to avoid leaking PIDs.
    - `--security-opt seccomp=unconfined` enables running without [the default seccomp profile](https://docs.docker.com/engine/security/seccomp/) for debugging.

## Contributing

[Contributing](CONTRIBUTING.md)

## License

[Apache 2.0](LICENSE)
