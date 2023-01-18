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
| `latest` | `sha256:fb7f94c95d10be6be3868fd68cd31dca1e42f5d099f44b31235e5eba9832f391`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fb7f94c95d10be6be3868fd68cd31dca1e42f5d099f44b31235e5eba9832f391) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:fb7f94c95d10be6be3868fd68cd31dca1e42f5d099f44b31235e5eba9832f391"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "340623a0244dd25835e315a7b743481b5bf82d20",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDXeNf/XMX8ktJZBTNnOPkt5wY/n5NDPCKkuSzp1dUm9QIhAMq8JBhqVkKaF4V9fZUYiPknyXE/uhMKkx8oVe7ZMK/x",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmNTMyOTU2ZjUzMjQ1ZjFkYzI5YTIxOWEzMjg0MGU1MTFjYmQwN2I2MTg2NWNkODY4YzEyYWZiYzE5ZmM0OWViIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQTBYWDBrZWJ6THFLSExvUUtVM3pWb0VoY3R0YkI4SjJTTE9tRVo2R1kwVUFpQnkvNzQ0VEwyMFFXQ05KdDBnZ2tDL1d2QTd4VmZhbUpSZW80ZG1SOHQxbEE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlIxVjJVM0pHZGtRMmNWQjZZVXN4WVhoaWFWUnZNWFZaTTJGUmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlRSTlJFRjZUMFJWTWxkb1kwNU5hazEzVFZSRk5FMUVRVEJQUkZVeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUzZGxrMFNrVkhjeXRuWjBaWVZXb3hXa0ZsVVhvemRUSXlLMmMwYUhSMFpXVXJLelVLUkUxdGRqZDNkblZSVkZKME1saG9aMnR0Um05UWEzZDJUVVoxZEd4eEwxVkxMMGxYTTJaUWNISjNNbUZRTnl0bk1uRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYwUTB0MENrdG9hVVF4ZWpGalMwRnpWakpRZG1SQlVraEtkVWt3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwT1JFRXlUV3BPYUUxRVNUQk9SMUpyVFdwVk5FMTZWbXhOZWtVeFdWUmthVTU2VVhwT1JHZDRDbGxxVm1sYWFtZDVXa1JKZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZUTFWSmVXRUtRVUZCUlVGM1FrZE5SVkZEU1VkNVduTjJielk1U1ZCR1FUQnJja0ZCWVVSVEx6Wk9UVEZWYTFvclpqbFRja3BVVGpaRFkzRmhlRWxCYVVGeFQyVjNjQW8yZGtwdlVFTjFaalZqUVhscFExQjBRM2Q2VEZGSlpFUnJOR1V4T1UxWVQwY3pWM1pCUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha1ZCQ25WaU1DdFdaVFZZWkdabVlXUkZha2g1U0dGbk0wcE9SR0ZVVEVoelVXVkRlRE41VFhKSlZHODRPQzgxSzBOc1pXTkVXaXRrWVZGb2JXbHdSR1pFSzJJS1FXcENVRFpPY205dFpWbG1abHBpUVRRNE0wWnNNV1p3VDBFeWEwc3pORkJrTVZSTFEzTlVhR1UwZWpkRU5IQnFLek5XT0c5aFpYTk5UVFZuTlRNdmRncDVVelE5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674002359,
          "logIndex": 11399069,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "340623a0244dd25835e315a7b743481b5bf82d20",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3944571629",
      "sha": "340623a0244dd25835e315a7b743481b5bf82d20"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

