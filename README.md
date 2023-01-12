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
| `latest` | `sha256:0889ccf5ad4bdb838f482838b52791716d0549387a111baf5c12aa87dc67e22b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:0889ccf5ad4bdb838f482838b52791716d0549387a111baf5c12aa87dc67e22b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:0889ccf5ad4bdb838f482838b52791716d0549387a111baf5c12aa87dc67e22b"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "21935e9c5956534e2381cb1061458df6382dd80a",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCEia/dnuas0EXxRnUJJvtK4H/6FsS49ww6YE7z8eHmqQIhANzbfbLmP9hYbJ+uiChs+ElpH+CE5DwWJQdnuMNku4ih",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwOThmYTk2YjZlZGM2MjVlOGFlZjE5ZjgzNjA0ZDA5NmZkMDRjYzM2NDNlYWM2OTQ3NjZjMTJhOTY4NDgzOWE1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQUZkY0lQTmdGTStETlJCUFdGcVZJOStpclRkcEcwNlpGQkdlWFpFWEhSYkFpRUExNWN4eTdrWTRTKzRVV0FWSFgvb2JiZW55QjY3dk1Iam9SdlBuUUxHM3RzPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlVVMHlPVzU2UWpKTEsycHdaVXB5YkVFMlNHNVliMGR1VVhkemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlhsTlJFRjZUMFJCTTFkb1kwNU5hazEzVFZSRmVVMUVRVEJQUkVFelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZYWm00M01XOXpaVk5DUzBzeVkzbFdhbUpIU0RCTE5ERlpSMkp0TTNvd1J6aHJVVklLSzNGaVVXOVZiVVpXWnpGWlRtUlNhRVZhVEUxclRtOU5jRkpaTmtKaVNtdDZkRnBRV0VkSGNGWkZORk5hTjAxbGVXRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMZERReENqVnFTVGx4WmpKNlEydHhUVlp3T1dOd2EzUk1jV2RWZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsTlZHdDZUbGRWTlZsNlZUVk9WRmt4VFhwU2JFMXFUVFJOVjA1cFRWUkJNazFVVVRGUFIxSnRDazVxVFRSTmJWSnJUMFJDYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYYW1GaFMxVUtRVUZCUlVGM1FrZE5SVkZEU1VSYVJuRkVUbVJYWmpsMVluSXpTR2N2VDFscmEyOHhMemQ0YWtWVFpHaDJVbUpWUVhFeFl6YzJZak5CYVVGVWREZzJOQXBEVFRKRVJXSndXbXBUYVdWRGQwdzBkRXBJUW1sdVoweGtSbEJaYTI5Q05HSnhXbkJDUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0l4Q2xscGJHaG9OSFUzZFZGM1NGcDBVVUl6ZFhwc05uVlFOVFYwVEVWa1dteE5ibFUzU210eGVtZFlRMHRMVnpjeVVsTlBjMjVNUkdwV05UZFVSR3h4V1VNS1RVTmliMnN2VjFReE5EbEVWV3cxUWtSdFFqTmhTVVJVY1hKVFNqUlBkMmR1VlhwVVpscEdTRTVJTjNvd1JGazFLMlJDWVZSNWNuZzBURkZ1Y21nMFJRcHdaejA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673483913,
          "logIndex": 10985482,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "21935e9c5956534e2381cb1061458df6382dd80a",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3897994759",
      "sha": "21935e9c5956534e2381cb1061458df6382dd80a"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

