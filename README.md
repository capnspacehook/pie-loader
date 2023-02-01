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
| `latest` | `sha256:3bc7a329be201a7dfc946dd8de05b9a0aef4f74de2b58cd394eb1368e0817646`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:3bc7a329be201a7dfc946dd8de05b9a0aef4f74de2b58cd394eb1368e0817646) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:3bc7a329be201a7dfc946dd8de05b9a0aef4f74de2b58cd394eb1368e0817646"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "98571b38897f600b0c8292627efdc9056c16d254",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCdTqOe8m9b2CWSAwtVvJpMClpOKdeqQ6y7n8f5Nr7SsgIgaxeR40nD5kKwVm6jjKI4yqobZNtKUt7PBkYRBfLE95o=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiZDViMGZkMGJjMDhkMTE1NmEzYmRjYTFjMjJkN2Y0YzRhYmNhY2UyODcxZmE1Yjg2YzM4ZDNmNzEwNzdjOTdhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURqaTZWd2F3OXhicVBISFk3SERDMnQ1SVpnbTZsd0h6dWNld0xTTmpWWHp3SWdNRzJROFhmS0F6a056Sm5FK2NKY2Q3NEVFVUN3RjdTMnJqaFh5b2gxVk5nPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVllub3hSMUpTZURKa1dtcFdWRXBqV0ROMWRtVjJXbFoyTVZKWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVhoTlJFRXdUWHBGZDFkb1kwNU5hazEzVFdwQmVFMUVRVEZOZWtWM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZMTWxnM1kzRk9NbUp6TTNoUFRWSkxNR2RvWldkc1RrMVNOVk5DYm5aVU1uUklWbkVLWXpZemFFOXJSMlppZW5WbU5tSkNaRmtyT1U4eVZXbEVWbVZOV25Kd2FFVjROa1ZqWW5aS1ZsSlBORlJ3UlRFMFdqWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzVGtsVENqTm9WVkJuV2xoT01GbFlZbXhwV2prME1FaDNjV3c0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWUFJGVXpUVmRKZWs5RVp6Vk9NbGt5VFVSQ2FVMUhUVFJOYW10NVRtcEpNMXBYV210WmVtdDNDazVVV21wTlZGcHJUV3BWTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaUzJKWVVHb0tRVUZCUlVGM1FraE5SVlZEU1VSNVpEQmxjV2cxTDA0M1NERjZORVpZZG5wMWRrUXdjVEppVGpCb1dVdHNhV2N5YjFoTmJUZHZaazVCYVVWQk0yWnFOQXB6TW0xaGJHSlZiMVJWYm5GSlpGbEhkakEyVVdaSk1ISmhjR281YUVaSWIweE9hV3gwTkhOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGT1pVbGlSR2xDVjNGeFkyZGpMMDVXVG5KT1NESlViSE5NUlVScGNtdDFVa1poYlVKYWJ6UldjelpvU0ZJeVRXbHpOVk54Y1VwS1ZsQTVPR0ZTUW5NS1RrRkplRUZMTmxjelMzTkVNQzlCVHpocVRURmlPV3MyUW5sbU9VMTRZVUZsU21sVlVIUkdNbU5xVURSRk0yaGhMMjl0SzB0MEwzSTNPVmR1TkVOQ1lncHhNM2RzZFdjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1675212211,
          "logIndex": 12370579,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "98571b38897f600b0c8292627efdc9056c16d254",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4059718876",
      "sha": "98571b38897f600b0c8292627efdc9056c16d254"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

