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
| `latest` | `sha256:029f64b225ff6700dd856d47af6ca5d59e9609be7190c4ad175e076e1749fcc5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:029f64b225ff6700dd856d47af6ca5d59e9609be7190c4ad175e076e1749fcc5) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:029f64b225ff6700dd856d47af6ca5d59e9609be7190c4ad175e076e1749fcc5"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "764698d7d5daeefdd82d0911e62648c87f80478a",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCbVtIWZLoZhPEiGLn/MW2BO3Z9QzF7v587zQr7T2SflAIgZglNhmFdtlp18TW1YzyKKf30NX7GChkiXLnf+lZPwmg=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjYzdiYjJmOTQ4NjBiMjNmZWU5NTU3ODZkZGY1YjI1MDFiMzRmNDc5ZWI4ZWU0YmFmZDkwOGNkMjQ3NTQ5NzYxIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNlZ2NnNUJCOXFTeHptTXBwWUk1OXlPMFVvMGlBSThkcXFTZGVXT2N4elJnSWdSK1Jhdit5b3ZaU09hc1l3akRINktZU3pWaGljTEkxd3JONTRrcXNxdFk0PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVldHaHJRMGRwVFV0bFVsVXpObTFPVlUxMVYxUjBWakEzVms5WmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1hoTlJFRjZUMFJCTkZkb1kwNU5hazEzVFZSSmVFMUVRVEJQUkVFMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZsZUc5emEyOVVOalJyZFZSeVZXSjRWVU5IVG5ST2JsSnJaRzVyYVZGQmNucHFZVWtLUzFSaU1saG5OMkZNYzBKUk1sWnlSek50TkZsTmVta3dMMkpHTkhwNk0wTnFjSFJXVEV4UloyRnNkbk5RZDB0UldUWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ3VVVKTUNtVmhWRk5uYWxkaGJXUjRSRkp6VVVsQ04wTlZaWE5GZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT2FsRXlUMVJvYTA0eVVURmFSMFpzV2xkYWExcEVaM2xhUkVFMVRWUkdiRTVxU1RKT1JHaHFDazlFWkcxUFJFRXdUbnBvYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZVW5kMVRua0tRVUZCUlVGM1FraE5SVlZEU1ZGRVQzWlJMMDFGZEVkRE5uZDVUMmRqSzFsdVZIaEhaVlZ0YkdoeFdEaDZRMVIxTkRGTFprNDFRbEV3VVVsblNqWXJkUXB5YVc0clJtSTRLMmxKV2tWaFNHbzBRMGd4V2sxSGRsaHpSWFl2ZUZwRlNGVmpRVTVWZUdOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2tvMWFXZGhhVE5sU25CNk5FNHhWbTVUWW10alNUSmlUbk0yVkhkV1IxRllkVlF6WkhKM0wwbERkRmxEUVVnMVUxQk1jMFExVmxvNGVXaEtUMVJhWVVnS1FXcENWbmRXYjI5VmVGWjJOMjQyU0U1d2R6VlVZVlF2WjB4Rk1YZFViekF2VjI1TlNUTTVPRE5TU2tsMGVrTjBOMGRGTW5KSlptMUVUbkpOVW1oVWFncDJlRFE5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674261515,
          "logIndex": 11616599,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "764698d7d5daeefdd82d0911e62648c87f80478a",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3972375582",
      "sha": "764698d7d5daeefdd82d0911e62648c87f80478a"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

