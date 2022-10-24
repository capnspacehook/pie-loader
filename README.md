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
| `latest` | `sha256:701c12c4c12263ba1afd7b8ba122dd369964bb787412dedf8fe7e363711b2a4a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:701c12c4c12263ba1afd7b8ba122dd369964bb787412dedf8fe7e363711b2a4a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:701c12c4c12263ba1afd7b8ba122dd369964bb787412dedf8fe7e363711b2a4a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f93b3ab3d31fdb4344beeae42d163171ebfd4504",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIQC0IO1kt7p3hY4OXp6+Y2CWdr3z8iXEFhqm6SWvyaA87wIffS/x3U0Q94GRa4Gf4OyoErgqlitxgAw1bN5C6LTzCA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJkNzg0NWNiZGYyNGJlYTI0ZjVhZDNiZDgzNzdlYjE3ZmZiOTgyYzk5OWYyMmI3MTYzNjZjZWRiMTk1ZjY0Nzc2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUQ1aTNQZEo4bVUxbWZzN2dUZXVCUU12MEU0N2xtTkducWFLajZpb3paL2ZnSWdIaU9wOTFKb2ZFVlZGRUp2Q3BnengxZXRzaUNNL1NSekpvVyt3V21RWjZVPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlZVTk1kMWhWWlZWQ05tdE1SVmx5ZUM5dWRVWk9WVmswZDBKamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1RCTlJFVjNUWHBCZWxkb1kwNU5ha2w0VFVSSk1FMUVSWGhOZWtGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZqYTFwQkszZFViSFptYzFoQlRUUTFWVVJ1VTBJeWRHRm9XamhsVlV4UGN6YzFSRkFLTTJaQ2MyVTBWWGh6U1ZCMWRFcE1TWFpCV2poeE1sSktRVzkzV2tZeGNrdDVNMFpzVjB4SGRrMVRWRGNyU0RsR1YzRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ3WVRoWUNqazJkbVEzTTNkU2NYWTVaRWhaYTNObFQyRkZXSFZGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxUFZFNXBUVEpHYVUweVVYcE5WMXByV1dwUmVrNUVVbWxhVjFab1dsUlJlVnBFUlRKTmVrVXpDazFYVm1sYWJWRXdUbFJCTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSU0djM2JFWUtRVUZCUlVGM1FrbE5SVmxEU1ZGRVZYSkVla05DTTJoS2NTdHpiM0Z2VERrMmRYSlhOSGRYY0d4aWEzQk9jRVppZEZaM0swTlRORlY2VVVsb1FVdHVUUXBsTXpoR1IyeFlORloxV2sxV1JqTkRkVlZrTTJ3MldtOXVVR1ZxYVU1amVWTnlkRTE2ZFdGaFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlJEWkVlVXhNZVZBMU1YRnhPR3gyYWpaRmJ6a3lVVVExY3pKc1RIRlRhRUkzYldVeGRXc3hZV0ZyTVcxb2NqaHpiR0pGZFVZMVF6VnFkRUZZZFZNS2JEZFJRMDFCVEhwRVRWSTBaSFZpTjJWR1pGcE9VVk5xTkZrMVYwSnhWRlJrVGtWWmMxb3JhRUp3WW0xUVVUbEVWblZ5WjFZMWVuWjBNM1ZpUzJOSlpncFhjVmhLU1djOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1666573404,
          "logIndex": 5730246,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f93b3ab3d31fdb4344beeae42d163171ebfd4504",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3309267307",
      "sha": "f93b3ab3d31fdb4344beeae42d163171ebfd4504"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

