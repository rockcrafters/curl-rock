# Curl-8.5.0 Rock

This directory contains the image recipes of Curl Rock supporting curl 8.5.0. These images are smaller in size,
hence less prone to vulnerabilities. Know more about chisel [here](https://github.com/canonical/chisel).

### Building the image(s)

> [!IMPORTANT]
> You need to have rockcraft installed in order to build any rock.  Check the [installation guide](https://documentation.ubuntu.com/rockcraft/en/latest/how-to/get-started/#getting-started)

Build the rock by running the following instruction:

```sh
$ rockcraft pack
```

Convert the rock to a Docker image using the `skopeo` tool:

```sh
$ rockcraft.skopeo --insecure-policy copy \
    oci-archive:curl-rock_8.5.0_amd64.rock \
    docker-daemon:curl-rock:8.5.0
```

### Run the image(s)

The image has the "curl" binary as the entrypoint.

```sh
$ docker run curl-rock:8.5.0 exec curl <url>
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:05 --:--:--     0

  <page_content>
```