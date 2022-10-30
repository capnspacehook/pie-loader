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
| `latest` | `sha256:a6152688db77525e59baaae86bdb5b2de4661b7ad488c6340b17079b577afd2f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a6152688db77525e59baaae86bdb5b2de4661b7ad488c6340b17079b577afd2f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a6152688db77525e59baaae86bdb5b2de4661b7ad488c6340b17079b577afd2f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "a45c2f893ecfecbb88e31261d8401e7b08260b44",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDz4I+bbFVGZk+2l1bBIkrI7+Z8GblQptR3SbAO9U9FdwIhAO/GHTusgaEsBeKbOt97dJWhfWoGXB5MKelis39FOnxh",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxNzdkMjIwOTBhYzk0ZTU1YzY2ZGYzOWQ2MjBkY2M5NDNjMmNiN2UwZWQ2Y2U4OWRmNjdlYTJiNmUwMGE1ZDYwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUR6SENaVkJtcXFzRUFnRjJQL3VseFdzb09SbmhBdFAzdUxtUnRUdi9IeXJRSWhBSUxQWnBtZ1cxNTZuRlE0QktKWnEra1ZmdTMzc3R5TDMza3BtYWowNzJvMSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlZHRXdhV0ZuYVhBd05sbEdMMlpRT1dWd1kwOTViVU5vY1VsRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFVFhkTlJFRXhUa1JOTUZkb1kwNU5ha2w0VFVSTmQwMUVSWGRPUkUwd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZzVUc5NVNYbFVORVJTVTNoeGNtbFdNMGg2UVZkSGJsbFBXakEwVnpVck9HOXZaalFLY2twWWJFUldLMmh1U1RSRFUxSkZNV1k1VTJOVmEwOVRZemxIZGtweGIzSk1MMHN3U2t4emREWlhUemhPWkUxak9YRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlU0UkROTUNrNVhUbFYzV0ZkbVN6Z3diQ3MwTlM5WGMxQm5LMDVaZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdoT1JGWnFUVzFaTkU5VVRteFpNbHBzV1RKS2FVOUVhR3hOZWtWNVRtcEdhMDlFVVhkTlYxVXpDbGxxUVRSTmFsbDNXV3BSTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSYlZsb2JXa0tRVUZCUlVGM1FraE5SVlZEU1Vkc01rdGpWVVJYWVVZdmIwSkNWVVpVU21oMGNXOUliMkpzUzJVeE16RjNRbU0xZG1FcmFsWmljbFZCYVVWQmNrZERNQXB2YzBKRk1tVldjbVV6UmpKM1NYaE9Oazk2WVd0T2VUQkxTbnBYVVRkTmVtbDBXRnBrTkhkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGSlRqWlBXbFpPYTB0amQzUTJURmRTZG1aUlZGcHplWFJoVkZOSGNDOVFRMjR6YjJ4RlpHTjRNRkl5TVZCVGRGazRkV0ZEZGtneFltUTJVMGRvWmlzS09YZEplRUZPWWpSS2QxRnFOM1ZOTkhKT1pESmxTbEo2V2pNdmFrb3lkV3BUVFU1Uk9WQldSR3BVZUZZclJTdFJOMjVtWkdodGJsQlhUWGxDYmpJeE9Bb3pibFZWUW1jOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1667091291,
          "logIndex": 6131684,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "a45c2f893ecfecbb88e31261d8401e7b08260b44",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3353566283",
      "sha": "a45c2f893ecfecbb88e31261d8401e7b08260b44"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

