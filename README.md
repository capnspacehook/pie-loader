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
| `latest` | `sha256:bfa579a0cc9886d5b267f034826fce715dccf4cf8e4f3fc0a03fba902f522d6c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:bfa579a0cc9886d5b267f034826fce715dccf4cf8e4f3fc0a03fba902f522d6c) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:bfa579a0cc9886d5b267f034826fce715dccf4cf8e4f3fc0a03fba902f522d6c"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7e9420c0daf55da5dd12b946b8af2485e9e8a127",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIA3uOuT8dAPcEOiBeMP5VlnOdWVh6n0/48SBGxSjYoGbAiBUdvAR7WVis3IPglirkA/hUvhZb/jNZPctBgNaDGV8GA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4YWY3YWY4YmE0Yzg2NzgzMDEzNzFmMDcxN2QyZDQ1YWYzMDc1ODgzMGY5NWI0Y2YwZGQ2YzBjYzI1Y2Y5ZmZiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJSHJIaFFDWFZmRzNnUzFOdDU2Z1hzMnVwblY0My9rTjJTOFVBWkNKY1hCMEFpRUErTkJCYk43WXYwNlM5MEFpL2QxanY5cEZBLzZkOS9zMDBKWldDdEo3djV3PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlpqUnRhVkZXZVRaTlNsbHBVbUV6VWl0RVExbE1URmRIVmxacmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVhsTlJFRjZUbXBSTVZkb1kwNU5hazEzVFZSQmVVMUVRVEJPYWxFeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZZVlhZM1JtSnNiWGxGWm5STlVXVldiMk16YW0xbVRTdHJhVlJpVjNadlUyeE5LMk1LY0RodFNGRmhRV0Y0YlhwT1ltWTBaSEIyY21SVVpuQjBaQzlZT0VGVWMwWjZNbWxSVG1wbkwzUTRWVTlxWWpkalMyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZIZVd3NENrUjVWREJLU2tsT2JqRkdNR3R4VlVGQmNEazRSMVEwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOYVZHc3dUV3BDYWsxSFVtaGFhbFV4V2tkRk1WcEhVWGhOYlVrMVRrUmFhVTlIUm0xTmFsRTBDazVYVlRWYVZHaG9UVlJKTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXZGpaTmJESUtRVUZCUlVGM1FraE5SVlZEU1ZGRFFqQlljR2N3UXpnMVZXTmtWM1pVU0Znek5VODJRMDUyTDBNdmIwbGlXV2gzZWxObFEweG5kbGN5ZDBsblpUQXZkQXBuT1c4eWRHUjVNRzlaSzJSMVpqTjJaWHAxVjI1VGRFVkVjMU5LTm1WcFoyOVlTV3RoZDJkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGTWNqRndSbGNyTXl0b0sxY3llVXN3V21kUlQwcEpUVEIyWVU1MmExRlJWVU52T0RsME1uUlVPRlJvY1dScFVIQklVWE56VlV0TmQyTlZTMVJHWlRFS2ExRkplRUZNUmpoVVVtazBTRmMyYlhOR2VHRldjbk5DTjJ4TVVWUm1lbE41V1ZWWlpsa3JhblpDWWxaUFZITldVMU5vZGlzMk1tY3lkVzl2TDNGYU5BcEtjMEZPTUVFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1672619830,
          "logIndex": 10288066,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7e9420c0daf55da5dd12b946b8af2485e9e8a127",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3819415539",
      "sha": "7e9420c0daf55da5dd12b946b8af2485e9e8a127"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

