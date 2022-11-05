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
| `latest` | `sha256:f2985390b4616fc83e7ac3b0fb916b555151bb985b865880d63fa17a9de6e1cb`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f2985390b4616fc83e7ac3b0fb916b555151bb985b865880d63fa17a9de6e1cb) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:f2985390b4616fc83e7ac3b0fb916b555151bb985b865880d63fa17a9de6e1cb"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "89d64be9bb0d2001b73c69f0e41a8ad884c2a068",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDcIcJqBAkMWm+Jh3I0cnOMZdy0Ow2V4GDaCnMlaKYi7wIhALxs+Yk7eanx4QTLXVSF0woknyxYxXGLMVgAf1ku8e1V",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5NjhkYTY3Y2ZmYjIxMzg3YWY4MWQ1ZTMyNzk5NzU2MDdhNWU4MTMwMjc1MDBmM2E4ODI4NjBhNGNhZGVkMGY1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJR0xmdjZ3ZGcyS1JyTEFyVTdPMVNOTSt1bVkyTUk5OHRkN2QvL2hYdHZQakFpRUF5TmVpTHcxLzcwOERyVXRTT0hzdGlNd1BpNUgvby85Ny91d1hPTG9BMlJZPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlEydGtVbE0zS3pCM1kybGhhalJrWmpWdWFtRjZhMmhzWmxWSmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVRGTlJFRXdUMFJCTlZkb1kwNU5ha2w0VFZSQk1VMUVRVEZQUkVFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUyVTNwNk16VTRiMGM0UXpsdVYxTnhXalJPVkVNd0t5OWxTMDFFTlhZMWQzUlhRUzhLVERkQ1JFRkdlV3R0ZFN0RFZUUXhXWGx5TjI1MVpISnFhVnBYVjJaQldFWjFWR0pwZEVRMFpFTkZjMlI2VDNNeEsyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZDTVM5RUNuTXpZemxOVUdOcU5WVXJPVXR1Vm5ndlVqaEZWVXN3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpSUFYxRXlUa2RLYkU5WFNtbE5SMUY1VFVSQmVGbHFZM3BaZWxrMVdtcENiRTVFUm1oUFIwWnJDazlFWnpCWmVrcG9UVVJaTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTUmxGdFNqTUtRVUZCUlVGM1FraE5SVlZEU1VGYVlsa3phMlZoVkhvMFZUZFBRbmh6VVU1amJFVnhOM1ZGVm5GcE5WTTRaRGRHYW5oRlFrUXJhVE5CYVVWQmFITnFTd3BhUzBSbVZFdEViVVJQUlZOdFVUSkZaVlJ4SzJKa1VFNU5WR3AzTDNoMk5EWXJWMFEyYmpCM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2tKMGVERXphMWczTlUwdmVrMVFTbk5aTldrMFNFb3plSEp1ZWxOdFZEUkVLMkpEUkRCVVRrNDRVREE0TkZaM056bGtWMFJEUkRFeWFYQlFURWRpYjNrS1FXcEJSbGMxUW5scVZsWnRPRXRqWWpZNGRIRlBVbkppT0ZCRlN6ZE9OM1pvWkZKMGNYTkRiM294WTBWVWFtOXRhVkIxSzBwdmNESnBVREZST1hwVWFRcHhUbGs5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667609309,
          "logIndex": 6528518,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "89d64be9bb0d2001b73c69f0e41a8ad884c2a068",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3398032488",
      "sha": "89d64be9bb0d2001b73c69f0e41a8ad884c2a068"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

