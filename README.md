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
| `latest` | `sha256:9e3a610f7b983e2e42c8665166c6e11ffa08b9bff00a3aa8d3cca8eabedba35c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:9e3a610f7b983e2e42c8665166c6e11ffa08b9bff00a3aa8d3cca8eabedba35c) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:9e3a610f7b983e2e42c8665166c6e11ffa08b9bff00a3aa8d3cca8eabedba35c"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "1d7437761dc1b7e6215e8831840df56002e21509",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCDh4zOA1nKHCjLSnoNCtJXgGAVTDiOhg24Fo6KohlvpgIhAL3rO4F3vFfHBRne8POx/RN8PJ1LQ/6iLZS/OzhDg+oh",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3MmFkNjVhMGZjN2Y2Yzg1ZWRhMjczZjE2YjNlNmQxNzlhZWNkNjM1MzNhZWIwYWMzYzAxZTYzOTRmMGVjNjRhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJSGg5bFZLbE1jcVhwUjlMVWxFR2g5cjRwY3FGWmNtYzljTmJQNHBBR3ZBTUFpRUE4bzNlTVFmU0QwWllUZ1dQQmw4TjVHS1hxWmpDbWs4L2VveGRTY0loNjEwPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlkzVm1XRzF4VVdoUGMyOUlXVVl3YlRWbFVERndPVFJTWmxsM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1hwTlJFRjZUbFJKZDFkb1kwNU5ha2w0VFdwSmVrMUVRVEJPVkVsM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUY0ZBdlJrbzFjMkpJUWpnM2JGQmpTMlo1WVZWTVRtSkljM2hPVVRZM1dFdFJPV1FLZW00emFrSjNWR2RCUlZvM1ZscHpZMjg1YlVjeUx6WnlNV3N2YlVwUVZuVm1hRWxTVFRCemNYQnJaVFJzZFhsNlQyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV3SzBKb0NrWlVPRVJ1SzJkWmJrWjFkazFDV0U5RGFUaEVVMnBCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoYVJHTXdUWHBqTTA1cVJtdFpla1pwVGpKVk1rMXFSVEZhVkdjMFRYcEZORTVFUW10YWFsVXlDazFFUVhsYVZFbDRUbFJCTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWT0ZvclYyY0tRVUZCUlVGM1FraE5SVlZEU1ZGRGNIUkJWMUIxU1d0MmIweDNNblpuTmtaclJVUXJaMGsxYm1wQlZUSldUbE53VjNSSFNtVlpTMHhEUVVsblNHOUVWQXBITkdsamFIbDZVRmd5ZEVKRlkwcDJNRkpMTWxkamRUUkhlbTgwUzJOa2JGZDVSV2QwU1d0M1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xwelptOW1aa1o1YWpWTGRURTFPVVYwTVdsT05Fc3dWbUl6TjI1TVRrNDVjM2xOYzAwMFFYUkJXakZSUjBGdlRXbHplVGR4Y0V0aVZIcFJjbTFDTlhjS1FXcEJVVUpRVURkU2NqUjNOMUpYYjJkc1dHeE5iR2Q0UVZSdlNqbFdaRW8zVFZvMlRUQnNaRmh6V1ZBd2VqSTRhMUZDYUZWRVJrZDZiM0VyVjNaSFVRb3ZWRGc5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671755748,
          "logIndex": 9656397,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "1d7437761dc1b7e6215e8831840df56002e21509",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3762173693",
      "sha": "1d7437761dc1b7e6215e8831840df56002e21509"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

