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
| `latest` | `sha256:99d53f1ff735aa51df7f6e211fe475d7ebf997a93129c810fa526be9cb4cf08a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:99d53f1ff735aa51df7f6e211fe475d7ebf997a93129c810fa526be9cb4cf08a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:99d53f1ff735aa51df7f6e211fe475d7ebf997a93129c810fa526be9cb4cf08a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "9644ddfbf951b59d41754f00a3710d9e21f05ea0",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFjuzoKfb0PkAeroQVR8itO4EhjPcIqBr9lFvypIop8UAiEA4Z27zpVvvUN0FniFQ8GhpTFeo9kw2hzPsXBTgoQzj0s=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhOGViM2ZlYWIxZmZhYzE5OGQzZGZkNmI1ZmQyNWNiNjdkNjdmNTVmNDgzNDgyMjU0YWI4NDY5YWQ3ZjEyMzJhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUQ0ckExbUpYbXJnMzU5bklhc3YzYkp2MGR2d3ZjY0tyem5iZUh0aTNFY0RBSWdZS3N4UnR2ZXdYaUUvL1BqNGwxZXh3MXZlcHYzMEZaV0g5WUtNSWppa0NRPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlFtZHNlWHBJZGt4S1F6Um5lSEJZWml0aWJIcG9XVGhCZDJSemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1RKTlJFRXdUbnBOTkZkb1kwNU5ha2w0VFVSSk1rMUVRVEZPZWswMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUYkZONmEzcHFXa012Y0hsSlVXZ3ZhRGRxTHpSVlpERlNXR1ZHZUZOSk5GVmtWbGNLZW05SGMyaFBOR3AwY1VFd05UTTNNREpXT1RGbGVuRnRiMjAwUjNsTmNuRkZTbTVWUkdGVGRFWkRSM0pEYVVNMlkyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZpYlhaVkNtbzJOM1JIUVVZMVVsVjVjVU5vZWpOT2IwaEljVEpaZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWT2FsRXdXa2RTYlZsdFdUVk9WRVpwVGxSc2EwNUVSVE5PVkZKdFRVUkNhRTE2WTNoTlIxRTFDbHBVU1hoYWFrRXhXbGRGZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSVW5kc1FtZ0tRVUZCUlVGM1FraE5SVlZEU1VOR2RqbDVMMUZUZVVvM01qUXJhVmhwTkdWSEswUkNOVU01YjJ3dk9VeEVhbFpNZUVKQ1VrOVFVMlZCYVVWQmEzbGtWd3B0VDFkWWRVSXJVMXBKTUU1Wk4wbDVWbFF3TVhCWk9DOUNOMDUyVkM4Mk5EQjVSRXhDVkdkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2tGYVJIVXZXWFpQYkc1Q1QyZDJjR0oxWkVad2JXSlJXVTF4WjA1bldsVlljazlOWTJKU1FtdFZUa3BXVW5WVFIwWTFibnBvVG5GVlEwdFBXRXcxT1RjS1FXcEZRWGxaVG5SbE1uazJNVmtyV0RKUWMzTklXRzFVZUZoVVRuQm9URGhTVkM5dU5FcEpXa0ZoYjJwblJXTmpOekpXYUZObU5uRnRObUpZV1hKWU1ncHBRa3BWQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1666745280,
          "logIndex": 5870583,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "9644ddfbf951b59d41754f00a3710d9e21f05ea0",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3325351588",
      "sha": "9644ddfbf951b59d41754f00a3710d9e21f05ea0"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

