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
| `latest` | `sha256:fc6081aa812834a97bd6bf9e2bbc450d0fe8cbe334471b7aa5d0bac5f510b831`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fc6081aa812834a97bd6bf9e2bbc450d0fe8cbe334471b7aa5d0bac5f510b831) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:fc6081aa812834a97bd6bf9e2bbc450d0fe8cbe334471b7aa5d0bac5f510b831"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "30f875499a6e86858f27ea4019c65e82e8af3a29",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDuOzCq4Hhv0BLAItMOUfGgWvRLmRFJKnbfJwB4O7NfUAIhANzZq4g2nmHNooXL5x+nFGlO9zzpP17/kkTm1/uG1K02",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwYmMyMjA4ZGZkMzczYTU2MGY5NGRjMzc4ODEyNTA1NTc4Y2I1ODQ2MDVmOGI1YTg4MjY1YWQ1M2Q0OGJkNzlmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQm8vYTh3M3hvdDliVEczcThrajNaV2IvMHRMMnFrVXo4OHVPc3paWUFhZ0FpQmZhWG5CNGY0NnRGQkNzcUVYYzdlTVlCTmtZUUdnZVE3ZkttL3pxdHVQV0E9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlJrSkRUU3RVUlRBNVNrWkpSVVk0WW1KSFFXcFpTRmRHYkRBd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1ROTlJFRXhUVVJCZDFkb1kwNU5ha2w0VFVSSk0wMUVSWGROUkVGM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZSWldoUFduRmFTQ3RPU2t0clQxVnFjekJIYnl0MmFEQlZPWEV2YmxVd1VYSlFTMGtLWVRWSk5sWnlWbFpOUkROS1VsTXJVR05aZFZsV1lrWlRRMVk0UkZaSllsWTRORWMwZFhOMVRHVjRRV05XUzFBMFdtRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZOYjFGbUNsUlJjSGszWkZadlRtOWFObkF5V2xaNVJtWnNWV1ZqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwTlIxazBUbnBWTUU5VWJHaE9iVlUwVG1wbk1VOUhXWGxPTWxab1RrUkJlRTlYVFRKT1YxVTBDazF0VlRSWlYxbDZXVlJKTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSVnpaMFoyRUtRVUZCUlVGM1FraE5SVlZEU1ZGRVdsQkROM0J0ZVdRME1tUk1RbkJJSzBOdFRWRnlhVGN6Y0d4TGNHdHdWVEZ6ZDBodGFVRktSRnBoWjBsblR6QlpkZ3BrTlUxNVQxQkhZblJXT1ZBcmVUaDBialppYmk4M1ltOXJORTE2WVZKbU4yTXdPVlptWVRSM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2tzcldFWXplWEZSVUVRM1dFcGFUR01yYmtka00xWkJjakl3T1RnMFVHTklVM054YWtaeWFGVXhPVU5VTkRBclltaHlSamR1YVZoT1NtRlVOM3BOVTJRS1FXcEZRWGxpWXpWMFVFWm1kM05xVWpOV09FbzNUVWwxWkdWWlNWQXlkVTVTWVRsSmNtNWpSWGRwYm5GNGN6TXlNSFJwVFhWR1JXMURhbFpOY1hBMk1RbzNPSGxhQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1666831824,
          "logIndex": 5944882,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "30f875499a6e86858f27ea4019c65e82e8af3a29",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3333649937",
      "sha": "30f875499a6e86858f27ea4019c65e82e8af3a29"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

