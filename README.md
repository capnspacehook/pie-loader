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
| `latest` | `sha256:4e0f3ce8db68af99f627c79c0f144c9b7b2212038182a154f4d57efaf594f6be`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4e0f3ce8db68af99f627c79c0f144c9b7b2212038182a154f4d57efaf594f6be) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:4e0f3ce8db68af99f627c79c0f144c9b7b2212038182a154f4d57efaf594f6be"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "2c1212c68ad28749f16d7824713b8156ba88cb05",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDhbOCLlxAdDW1+Ly6pXddjkxEioVdGLs5ZbkUnLjMFfgIgRLnzyy+YkBcjQCAR0yNbiuqpHrgFsCYPf4Kt0hsNAPU=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjYmMwMzI4MTE0ZmQ4OGVmNjY4YjYzNmI1NTk5OTQyZWRiZTE2MmQwZmI3MTJhMzI2ZGQyMTFhOTEwYmEzODYwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURudm1EaW1WZUgrd3BtdTFrZW1pR0huTmlqZUs0V2tiTzk5WlJhWE5Wc3JnSWhBS1J6b1hhbmp6OGJYeWl1NklCeVc5NHdldzNZKzV6N2xmdGdJa3lIa3MvSiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCaFowRjNTVUpCWjBsVlVXNHJRMmRaVW5WRlJtTnhjV0YwYVVRMFZEbHljbmhEYjI4MGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1ROTlJFRXdUVlJWZWxkb1kwNU5ha2w0VFZSSk0wMUVRVEZOVkZWNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZPUW1OQ1VHOVVaR0pvUTJzeU5sWlZNMUZIUmpOb2NUZEJNV1pwUldKaE1HNUhibWtLUVVaaVRIb3JVVzFOV0ZsYVdpdGtTR2RhU0RoNUwxaFVZbWQ0ZUhGVmRrOURXRXRGTDJJM2NEQTNRVXhUYlhST2MzRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUyYURSVUNteDBkWGQxTlVzclRqWTBhamxxU0RCbVUzaHFPR3cwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsWmVrVjVUVlJLYWs1cWFHaGFSRWswVG5wUk5WcHFSVEphUkdNMFRXcFJNMDFVVG1sUFJFVXhDazV0U21oUFJHaHFXV3BCTVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUTW1sSmVtY0tRVUZCUlVGM1FrbE5SVmxEU1ZGRVdraHFSazFKZWtKbU1rMXVSa1ZQY1cwd1VqWkROVXA0ZVVRdlVYcHZlbVF6TUZoUFpGVkhiR0pYVVVsb1FVMXZNUXA0V0haSFVIWnFZbHBKU1hwaE5VZEtiMmM0UmpKb05ubGFWbVJYZEVOVFdsaFBSa2NyWkd3eFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVkwRk5SMUZEQ2sxR2EyMHhibkJxV21Vdk9XVjJUMVZET1RJMVVFbGFWVFZyUTBOdU5pdFpSamhQUm1GYUwwa3hVVzVvWlhWeVRrRlFlblZtT1dsTFJrRkNUM2c1YzBRS1IxRkpkMU5MU2pKbWJWaHZTa1J1UmsxMVRrSklXQzhyUTFFNWJFRjFURmtyYTBnNVYweGFNMGREU25OMWNVVXplbFZGYjFNclJtMUdabTlZUzJ4RFpBcGtObEV5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669509731,
          "logIndex": 7919002,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "2c1212c68ad28749f16d7824713b8156ba88cb05",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3556037116",
      "sha": "2c1212c68ad28749f16d7824713b8156ba88cb05"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

