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
| `latest` | `sha256:1b65da2404659483f6702a6cd9163cd6efaf67ca2096893e5f7023d728b522d2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1b65da2404659483f6702a6cd9163cd6efaf67ca2096893e5f7023d728b522d2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:1b65da2404659483f6702a6cd9163cd6efaf67ca2096893e5f7023d728b522d2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7ceba43e9fbf9b75ad3e4993a3d4f69d282f6900",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCn44s3q6jjyFXktr/c0aqXk7/kVhdgAlfD1/R0xUBDOgIgcPSgDfTDb+3G60LZorxYBmp+TiiS2aX6SaZjsow1zww=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiMmI0MGZmNDU0ODgzYTllY2M5M2E2NDI2MDAxOWRmYTMzNDk4NTY4NWY5NmIzZTYxZWQ0ZDliMGI3MTIxZTA4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRGt3MzA4bXVzYWZWQmlkd0d6SVpOdk5PZGxpWUtwaWRNSm1mYS9ET0F3K0FpRUE2aHBzSjdoRXVxZGloZkh6ajl0QVg5WFd1UCtWTnlMWXlGOXVBUjlFWFlnPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlRIaHFRalV2ZG14eWVIUTBSVVppZUd4b2FGVmlPRkZLYzFwdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlROTlJFRXdUVlJSZVZkb1kwNU5ha2w0VFZSRk0wMUVRVEZOVkZGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZWZEN0QmNITm5aakZzVG1sU1dVWnRjeTlvVWtOSVZXTlVlbUptVG5sMVIzbFdkbFlLTlhsalNuSlFkbU5LZGtrMVkzWllaRGxoVVZGV1NVOVdaR2wyTUVaaFVYTTVTWEp4UzFGb1puTTBRVmR1ZFhWbVpXRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzVjJSbUNrOVRaa1ZJTUZrMk1EWlZhRWRoT1VoSVFURkxiV1pWZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOWk1sWnBXVlJSZWxwVWJHMVpiVmsxV1dwak1WbFhVWHBhVkZFMVQxUk9hRTB5VVRCYWFsazFDbHBFU1RSTmJWa3lUMVJCZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUUkVOTk1YUUtRVUZCUlVGM1FraE5SVlZEU1VkVFlsTmlSblF2Wld4SmJubGhRMFEzY0ZCUE1uTjVNRGhOWTJkdmEyTk5hekJQV1ZkdlkzQkVRbEpCYVVWQmVreEZOd3BKUW5SUFQwVXdNbmhCVGxSRlFYWlBNelV5UVZCNmFsTlRNMjlPTlVwQ2FuVkVjRVJhTjJ0M1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTFJUa3pSR1pDU1ZCbFNVaEpka3R2ZFhOWE0zWkZlWEZ2TWs1SFdsWkVTU3QyS3paVVRqRmxPSGszWjBvNVptWlhOVFZLUVdreVEwRjRUSHB2UzNnS1oyZEpkMHhCTmxsSVJtY3JkbFZMUlhoMFFtSXJlRmREUzBoRVJGVnliVnBwVUVjeE1YSlhRWGRNT1d4c2J6VlZiMDlHUjJSbU5sUTBkM1JRWTBwWFFRcHNRUzlKQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668645736,
          "logIndex": 7239529,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7ceba43e9fbf9b75ad3e4993a3d4f69d282f6900",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3484338541",
      "sha": "7ceba43e9fbf9b75ad3e4993a3d4f69d282f6900"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

