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
| `latest` | `sha256:85e8cebe2651875999ca4c720b9623ef9b38b8cecf03598083e4a8a8576146ab`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:85e8cebe2651875999ca4c720b9623ef9b38b8cecf03598083e4a8a8576146ab) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:85e8cebe2651875999ca4c720b9623ef9b38b8cecf03598083e4a8a8576146ab"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f2760a128e6ec167d3a23ba18260380760e5b049",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQC4nrFItcCm9AVhanzA+ZKivB8j48DCU74Zw56Ri+5xggIhAOSmxLaDtDrA4RbHJhlNdx0BTLS17LKWWIG3nuMLV8Kz",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1MzdkZjFmOWNkY2ZjNTA2MTRhMWYzYzJjZjdiOTdiODcxOWNiMGQ4NGFiMjZiYjE3YThhMmJiOTExYWU4YTdhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQkdlSFJpYmp3dTUzTXlLZk9CeXFJdWpnRkpSMzJiR0FRM0lrYTBteTlUS0FpQmNuTzF0am9QRGtRMTh5Zi8rZFRJbk50T3hVeG1SRVBBM1BtU1pPWXdaZ2c9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlZUSlVhVE5UU3pCT1kzRlNkVEZpVUhKeVQzRTNOVXB1WlVKcmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1hoTlJFRXhUV3BSTUZkb1kwNU5ha2w0VFVSSmVFMUVSWGROYWxFd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZsZVZvelJUY3hSekJ5YVhsNEwydFNRVmgwTkhoT2FYZENRMEZpWjJ4TFRreHNiMklLVjI0MWFXaFhMM0pPVkhWYWIxSXliamR2V2s0M05HRXhRa1F2YW1KbFNteHFNRWhoUVZCNFR6UnhhVU5CZGpFd1lXRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUwUkZwS0NtNURVelZUYVhWVU5tbE5RVUZoYTA1VWEyUmpiMjQ0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxTmFtTXlUVWRGZUUxcWFHeE9iVlpxVFZSWk0xcEVUbWhOYWs1cFdWUkZORTFxV1hkTmVtZDNDazU2V1hkYVZGWnBUVVJSTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxRTkVKNUswb0tRVUZCUlVGM1FraE5SVlZEU1ZGRE9HSTFaa0pzTVZKWlZHaFpOREpPYUhwMFZFbEpkVXRLYUZWamVXbHdNbXBWYzBGd01qZDRZMDB6UVVsblRqRTVPQXA1VEZOcWJVOXdVVVF5WkZreU1qQm5UVTlKYkdWdE9IUlFkWE52TjFVMFJFRXlXa2hZUTFGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2trdlV6UXZLMFZ0UkV0TFNqRkpORzh3TTNSSFpFbElkR2xYYmpreUwzWjBZelpOTURnMFEzZENjSFF3YkZadU5rcFdaMmR3VFd4TWJGUk9MMXBhSzNrS1FXcEJSemh2YzJJdmRrVndZM0FyZDJacFVtUTROMk4wU2poYVQzcEpZemt5VFRoWU0xTmxZWFo0YTJ0TlNrdG5SMmRMVEhJek1XcDZlR3RuUTB0UVVncFNLM005Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1666313592,
          "logIndex": 5529214,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f2760a128e6ec167d3a23ba18260380760e5b049",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3293982048",
      "sha": "f2760a128e6ec167d3a23ba18260380760e5b049"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

