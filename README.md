# Hadolint Example

This repo shows an example of linting a Docker file with [Hadolint](https://github.com/hadolint/hadolint).

The repo contains two Dockerfiles, the original Dockerfile which hadolint identifies issues with. 
Run the command:

```bash
docker run --rm -i hadolint/hadolint < original/Dockerfile
```

This command produces the output:

```bash
-:6 DL3018 warning: Pin versions in apk add. Instead of `apk add <package>` use `apk add <package>=<version>`
-:6 DL3019 info: Use the `--no-cache` switch to avoid the need to use `--update` and remove `/var/cache/apk/*` when done installing packages
-:11 DL3047 info: Avoid use of wget without progress bar. Use `wget --progress=dot:giga <url>`.Or consider using `-q` or `-nv` (shorthands for `--quiet` or `--no-verbose`).
```

See [rules](https://github.com/hadolint/hadolint#rules) for more information on
how to fix these issues.

Note: when pinning alpine package versions it is useful to refer to the official 
alpine package management site [here](https://pkgs.alpinelinux.org/packages). Also, 
it is possible to idenitfy the versions of packages by building the Docker image 
without pinning the versions and then run `apk info *package*` within the running
container to see the version which was installed without pinning.

To build the Dockerfiles run

```bash
cd original && docker build -t bvwells/hadolint-example/original .
```

```bash
cd updated && docker build -t bvwells/hadolint-example/updated .
```
