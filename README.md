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
| `latest` | `sha256:0dce12fc20121cb8d58e2a36473f91558d254854dc0039909d7f7558ee0a760a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:0dce12fc20121cb8d58e2a36473f91558d254854dc0039909d7f7558ee0a760a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:0dce12fc20121cb8d58e2a36473f91558d254854dc0039909d7f7558ee0a760a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "push",
      "1.3.6.1.4.1.57264.1.3": "0f1bf9ecc709caedd7bce429e28fd4761f0197a8",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDauNf4JknyiVHlYE6uRvNKQPwXwNwKi3OXj0tFFbKvowIhAJoFM7yfGSH+iKcw6ZZCusZ9UrwUkh1ypbv06+WaDmG2",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzYzkyY2EyMWRkZDkyMjNiMGIwMGE0NjM2NjMyODQxMjczMDdiNjU0YWNlYTlkNTgzY2EzNDUwNWU5Y2Q1YjdjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQTlsbUdmTDdVMEFvZTB3VzFKSkZCMVpVYVlEQTMzZTlMcjREWDFJVFd5UkFpRUF5RHZxTXp1Ui9FcHJ1akdaRlFPT2wvZlphWU9tcDRNVWVjQ2NTMmIvckVrPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJSRU5EUVRCSFowRjNTVUpCWjBsVlVHeHhXREpaU0c4dmVYVXpSbm9yT1c5TksyNXBVRFZwVEhwamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRWTmFrbDVUVlJKTTFkb1kwNU5ha2w0VFVSRk5VMXFTWHBOVkVrelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUwSzNCM1lucE1ZbFpUUjA5U1V6TlZTWG8zVHpoUWNIQkdVM3BIVTJWa1pFWmxXRUlLTDJkMVZVZEljVmR0VDJkbmJWRk1heXRpYzFOSlFWTnFkRTR3Tmt4V1RIZDRXWEp1ZVhOb2VHdGpVRVo0V1hCNVNtRlBRMEZ0UVhkblowcGpUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZKY2psTENuQmhNVnByVjBWMU1WZElNMkYyZVVJMGJVSTVlRzFKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGVFFtZHZja0puUlVWQldVOHZUVUZGUTBKQlVuZGtXRTV2VFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUkNiVTFYU20xUFYxWnFXWHBqZDA5WFRtaGFWMUpyVGpKS2FscFVVWGxQVjFWNVQwZGFhMDVFWXpKTlYxbDNDazFVYXpOWlZHZDNURUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVV1ZNYldSd1pFZG9NVmxwT1ROaU0wcHlXbTE0ZG1RelRYWmpiVlp6V2xkR2VscFROVFVLV1ZjeGMwMURXVWREYVhOSFFWRlJRbWMzT0hkQlVWVkZSMGRPYUdOSE5YcGpSMFpxV2xkb2RtSXljM1pqUjJ4c1RGZDRkbGxYVW14amFrRm1RbWR2Y2dwQ1owVkZRVmxQTDAxQlJVZENRa1o1V2xkYWVrd3lhR3haVjFKNlRESXhhR016VW14amFrTkNhV2RaUzB0M1dVSkNRVWhYWlZGSlJVRm5VamhDU0c5QkNtVkJRakpCUVdobmEzWkJiMVYyT1c5U1pFaFNZWGxsUlc1RlZtNUhTM2RYVUdOTk5EQnRNMjEyUTBsSFRtMDVlVUZCUVVKbkwwcFhWa2gzUVVGQlVVUUtRVVZqZDFKUlNXaEJUSFIxVFZnME1GcGxkVTAwVkdaYWIyaEhNbGxhVTJkeE9YVm5NMUJ5ZUN0S1l6QnJOVU5vYWs1Uk0wRnBRbWxtYUVkV01FZE5NQXB5Vkc1cEwyODFVMWhRYm1nMlVUVjNUVnBRU25GelRGTkZOekEwTlRKc04yOTZRVXRDWjJkeGFHdHFUMUJSVVVSQmQwNXdRVVJDYlVGcVJVRXJaR2hsQ2tObWJGcFVhWGh1Ym5aSVJrOTZXRmQyUlhOU1pWVllNR2hsYkdsdGIxWkZSbXRxVFRoTlJIVlVVWFo2TWpWdFVHMUpaRWhvVHpsNVpVdHdjRUZxUlVFS0syMURPRnBrZWxWbVZXMWpRWE5tTUZGNWIySjJObTFZVmpSRWFtWnhiMVpZWXpBck5ETkhXR3hUYWtKbU1HMURiRkp2UkdOd2FuZEJkbWxSTDNoWmNBb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1666218135,
          "logIndex": 5458066,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "0f1bf9ecc709caedd7bce429e28fd4761f0197a8",
      "githubWorkflowTrigger": "push",
      "run_attempt": "1",
      "run_id": "3285379413",
      "sha": "0f1bf9ecc709caedd7bce429e28fd4761f0197a8"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

