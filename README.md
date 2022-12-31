# pie-loader

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/capnspacehook/pie-loader/actions/workflows/release.yaml/badge.svg)](https://github.com/capnspacehook/pie-loader/actions/workflows/release.yaml)

Distroless container image for running statically-linked PIE binaries

## Get It!

The image is available on `ghcr.io`:

```
docker pull ghcr.io/capnspacehook/pie-loader:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `latest` | `sha256:1f249c9427ab61da15c623a0b34dd8d6537213ea739b34bc751d6112fbfdaeb1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1f249c9427ab61da15c623a0b34dd8d6537213ea739b34bc751d6112fbfdaeb1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


## Usage

Use it as you would the `scratch` image, just copy your statically-linked binary in and set it as the entrypoint. Only `musl` and `libc6-compat` apk packages are installed so PIE binaries compatible with glibc or musl can be loaded and executed.


## Signing

This image is signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify ghcr.io/capnspacehook/pie-loader:latest | jq
```

Output:
```
Verification for ghcr.io/capnspacehook/pie-loader:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/capnspacehook/pie-loader"
      },
      "image": {
        "docker-manifest-digest": "sha256:1f249c9427ab61da15c623a0b34dd8d6537213ea739b34bc751d6112fbfdaeb1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "44224f09649e46e36f1b5b37e8577c49f5cb580e",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCCDdkPqwmR1WLfukt4mIC066N9KBw2Sja7rKEM3U4wlAIhAPMDK3Cbx9pn/00lS6NjPeWzGBPXfR2ZQIWBQ4N56XBi",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwNmQ0OGQ5MzdhNGE0Yjc0Mzg1MzI5Y2JhOWYxOWE4MWU3NTE4YTJhZmFiYTk4NWQwY2FjNjE0NmNjMDVhMTQ3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRE1YYkZaaVRwcjBIelozNUF5NTZjTDZnU0UydWxQWTIwWXZ4bnk5UlZJZkFpRUF6V1dxNktNZXV3NVhGU2RMQXJkNnZ6MjJ6WGxBZHRoWHcxR3R1Sjc5a0pNPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNWRU5EUVRCaFowRjNTVUpCWjBsVlVURnpSelZVUW04NFNrNVRkamxoVVdWSlZFNXNlaloyZURsTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxVFhoTlJFRjZUbXBCZVZkb1kwNU5ha2w0VFdwTmVFMUVRVEJPYWtGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUZWxSVGRYSnplbll6YUZwb1JrMURjSFl5VUhnd1kzSnhNRTlpTkhCRFdVZE5kMDhLUVRWVVZsRjJWbGxqWkc1SE1tSnZhVFkyVDBvNFlrRlRSRGxSYVU5dmJFdzRPRUZhWlVGRVZsTXdlREZxWjFoTGFYRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZoUnpsYUNtOWxlRW94T1RjM1NuQXZUazluVm14M05tcEZaV3huZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCT1JFbDVUa2RaZDA5VVdUQlBWMVV3VG0xVmVrNXRXWGhaYWxacFRYcGtiRTlFVlROT01rMHdDazlYV1RGWk1ra3hUMFJDYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXYkcweWRqUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRFlYQmFXRmRuYlhreVkzQldVWEE0VmxNd1NDOUdUQzlWU2l0YWIyWm5aVmxvVTFFd1J6a3Zkbk5RVVVsb1FVbDROd3AxU21wSGIydDBNSGRCVkRCVGJERkphMHBOTlU1cFFsRnRWMjFJY2xOaFNqWkVMMDFyWWxwTFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeWEwRk5SMWxEQ2sxUlJEVndNak5pVUVWRWNrbzBXVE5oZFhKMVdHUk5lbEJZT0d0bVRsbDZXRVF3UTFWNFpGUk5VMncwVGpWVGVuWkJkMVJ2UjJ0b1IzQldPVTlQZVZZS1NqaHJRMDFSUkdrNWVGSXhhazUxYW1JNFNHdFJNamhUTkRWWlpVeEtXalkyYkVwTlJtc3hZVVZhY25rMFlrVkdWRlZUV2twVGN6ZHVjVzA0VGxaaWVRcFNURVZ3ZFN0clBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1672446995,
          "logIndex": 10168076,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "44224f09649e46e36f1b5b37e8577c49f5cb580e",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3809825755",
      "sha": "44224f09649e46e36f1b5b37e8577c49f5cb580e"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

