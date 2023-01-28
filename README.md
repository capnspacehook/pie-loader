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
| `latest` | `sha256:fc0252bd15d913a1bbe121bc552646848955e7967f44bb8f1cd2469f758dd629`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fc0252bd15d913a1bbe121bc552646848955e7967f44bb8f1cd2469f758dd629) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:fc0252bd15d913a1bbe121bc552646848955e7967f44bb8f1cd2469f758dd629"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "88aa1a7504547cc9cf9dc90b6271fd0446bc83b5",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCYwsaPyIwvpGEF4h0YdXslAkUSgzNuT5yDb5f27KdhzgIgRhDFqc4keRf8K1NSURElkx34T021+PU5vy31grY+JUw=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4MWY3YjEyNTFiZGNiNzI4Mzc0N2U0ZDZmNzIzMTYwMGIzYTI1MTBkYzU4YTZlZmEzNjg0YTI4ZTJlZjJkNTFmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRkxIdDBWYVFCQ3pRSC9xZ2R3ZjVVZDhNRjU5K1JrUjhNTEd2RjV1YlRyL0FpQnJnbjFjNmtGRXFwQXQvMlJvMjlyMkZLTzZpS3Z3ZXZvN0NWWHRCNFpqV2c9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlNteE1SbnA1V2paNGRIQTFaekJqZEVRMVpGVmFTRXh2WmxkemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1RSTlJFRjZUMFJGZUZkb1kwNU5hazEzVFZSSk5FMUVRVEJQUkVWNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYwVWpSRmJDdG5kV2hLZVdOWGVUVjZkVkoyVm5kd1NFWnBUWHB4Y25SYWQwd3pRVU1LU0c5TlkySkxRVkJvZDJacGIyaHJNMFJ3YlVkVWJFeGlVMUpIV21wblNsUlpTMHRwSzJkWGRVZGhTRWRMVUhnNVRFdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY1VWxwVkNsUXlaemRhYVhwNWVtSllOMFF5T1hkNkt6QnJSRmh2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpSUFIwWm9UVmRGTTA1VVFUQk9WRkV6V1RKTk5Wa3lXVFZhUjAwMVRVZEpNazFxWTNoYWJWRjNDazVFVVRKWmJVMDBUVEpKTVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZTVhvelUwZ0tRVUZCUlVGM1FraE5SVlZEU1ZGRGRUaHZWa0l4U25ORFVqVTRTSFJVZGtveGFtdHZRM1pIT0hFMlVIbzVMMlEwVG1wNE9Ia3ZjMDloUVVsblIzZzRTd28xVFhSR1pFSmFNa3BSZUdwME4yUkpLM2cxUlZFM1oxbFZWRFIxTWxwVmRGVm9TRlkwU2tsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTGNISjRiRXh3WVZnMVdUZG9XVzlTTTBKdGJYbG5MM2xvVnpacUt6aHZUMFpWZG1scGVWSXhUbHByWVUwdmRtMVJOVmhsU0M4MUx6TTJRVFpqWjJRS2RtZEpkMXAwY25kR1VrVTRLMDFUYkdkSmVVSklTVzl5TldoNVZqQjZNUzl0UzI5c1ZYQnFOMDFMU0c1SGFXTnNiMjlVY21kc2RVWnhRVEYzVGxST05RcFZOVVJCQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674866320,
          "logIndex": 12099294,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "88aa1a7504547cc9cf9dc90b6271fd0446bc83b5",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4029292651",
      "sha": "88aa1a7504547cc9cf9dc90b6271fd0446bc83b5"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

