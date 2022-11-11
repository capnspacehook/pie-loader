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
| `latest` | `sha256:5f660a9ad8fadbb821d5513a84053ba694594c694c9736d9f2fabc1610c36f65`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5f660a9ad8fadbb821d5513a84053ba694594c694c9736d9f2fabc1610c36f65) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:5f660a9ad8fadbb821d5513a84053ba694594c694c9736d9f2fabc1610c36f65"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c3e0b8102043e9bc0d427ed82865a15a33e71d52",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIGjX7lO5ySWDR2oGvty22wU1smTL+40qVRcfa2QebibCAiAGETA5DDCRioGocAB6dOvNm6Fvb1kRXUKzPCGsuITb3A==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjYjBmYmI2ZTIwYmQ0M2VjZTEzNmU4YjA1N2NiZjI5Mzk0OGFhNjNlYWVkZmEyNDc4YzBlMWU5N2NiOWIxNDQ4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRk5JMmpiUk03cUwzWmtrTDNENlV2NVBMZmYvdGIrelZuYVJBcmZJY0lvT0FpRUEvalFiT2JWcTJxbkZDUEllTWt0Mktjeko3SUpLSlJoUS8xK0VyNVZYbzhzPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlVGSlFNa2xXZFRVMmRsbExhamxEZVZST2RIWmtVV3gzZG1KcmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlhoTlJFRXdUbnBSTVZkb1kwNU5ha2w0VFZSRmVFMUVRVEZPZWxFeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZTY1ROS1puSldNVUpqT1RSV1FrbE5NQ3RxZUVSaUwwaE9jR3d6UW5OWmFtcE5RazRLVm1SQmFrOURZMWNyVVZBelVEQnphRkpZVWtkQ1JuY3ZVRkZJYjA0NVkySkJXV2NyY2tNeWFETnBaM0EyVGtWUFJqWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZYWW1aeENrUXpaRkZXUlVKU1F6YzRjVmxVU2l0d0x6UnlUbTR3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwTk1sVjNXV3BuZUUxRVNYZE9SRTVzVDFkS2FrMUhVVEJOYW1Sc1drUm5lVTlFV1RGWlZFVXhDbGxVVFhwYVZHTjRXa1JWZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTYTB0RE9WSUtRVUZCUlVGM1FraE5SVlZEU1ZGRGQyWjFTMlJLVjA5T1lUazBTRXRxVWxkck1qbG5TMFJZVFVjNVFURnRXRkZRZDBScGFGY3pVbEl4ZDBsblZYSkhVd3BHV1dkNU5YVTFSVWhSVlRNd1NVaFZSbFp1YTFsR1JsUTNjVUZLT1had01VdFVOMGRGWVVsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGUGRFSXpZbmxTYVZvelpHTkZPVTVqZVRCWGJFSmplbkZZZFV0TVFXdElRWGg0UVhOSWRsUkxXSE5aWmpkNmFpdHdWRkZCY0RsNlZsVlZUV2RYT1VzS1JXZEplRUZRTjFOS09FeFVORU5DVTBSSk5HZzVVR3R0VVdaMk5tbHFZVnA0T1UxUFZHUnlkRFlyUm1kRFpUZ3hhbVZRZWt0aE1tMU9NVkJUVERObVVncEZSWFZ2ZFZFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1668127688,
          "logIndex": 6847901,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c3e0b8102043e9bc0d427ed82865a15a33e71d52",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3441594954",
      "sha": "c3e0b8102043e9bc0d427ed82865a15a33e71d52"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

