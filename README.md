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
| `latest` | `sha256:c0ebb37b7cac369de916d452d80f0330aeaadf8a7a81441421503697bd373fc8`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c0ebb37b7cac369de916d452d80f0330aeaadf8a7a81441421503697bd373fc8) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:c0ebb37b7cac369de916d452d80f0330aeaadf8a7a81441421503697bd373fc8"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "8ec5ad60ad83bb4eda6826aa828272a2d9cd62b9",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCAt0LZDpegbYfJxEtqRFX6FEGOx/ZnTYuI3CJ5YMo/QAIhAJr9mpYWYm50cBKNDhfQNUAnSguH2cvuZdKJlRDM3rZS",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3Y2JkNzEzMGM4ODFiNmE5NWIwNWQyMGJmNmQ5M2EwOWVjMjdhOWM4OWI2MTI1OGYzNmVhNjA4M2M1MTVhOGRiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUN5TVRBczRmS2ZmYUd4aFN6Y0doNFRSMjVocmJYeEczbk51bnRrRDdiL2tnSWdOb09URkxQSURsZTBCcjZWa2h5ZGQ4a2RZT1dKS1JwSWE5a0FFSXhra1ZZPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlYzZEZNMXBYVDBWcFVXWkVSMmhoTWxKQk5tRkZZVTEyYjI4NGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1RCTlJFRjZUVlJOZVZkb1kwNU5ha2w0VFdwSk1FMUVRVEJOVkUxNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYwZEZWeVEyUnFRelp6ZGtnMVZEUTFNbk53UW1zNU9WbFpiMW8wSzFwRFJWbFpTMGtLZGpaeGR5dG9LMUJvTVRSQk0wY3lUSEJqZFRabk9FcEZNRzFvZW1sVVMxUTFXaTk1Y21KaVRWTmxkbXhLZHpaSmIwdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZHVW5NckNtWndWak4yUTFSNFRrVmliVTR3ZDNCa1JreG9LMXB2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpSYVYwMHhXVmRSTWsxSFJtdFBSRTVwV1dwU2JGcEhSVEpQUkVreVdWZEZORTFxWjNsT2VrcG9DazF0VVRWWk1sRXlUVzFKTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXUW1semJsZ0tRVUZCUlVGM1FraE5SVlZEU1VSTU1sSlJaakprZFdkcVRrbzRPR0p5VEdOMlYyTlBNVVI2ZEd0S1lrdzJTa2RZYmxoWlpUZzVjVzFCYVVWQmRqaHRTUW8xUTBFNFkxTkNiVmR4WVZaWVNqRldiVUU1WjBwMFZURTJaQzlZYnprdmVEZE5OMHhJZEhOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2tSRWRtTkhVSFkyVkZkcVozbEpUV1JoZW5KSksxUjBUV3hrWW1sd1Z6YzNha0o1WW0xWVIyRnZlVXRYZG10bUswUTFhVk5zU1VvMWVGUTJlV1ZEYTNjS1FXcENVSEE1ZUc5TUwzSmFiRXR6Y0ZnMFlrMUxNMGhWWVhFeGNGbEJWamxtY3pFMWVrMUdWMUY0ZW5rMWJWVlpOVTlvUzNwemRVZzRZaTlLVW5WU2J3cDRLMWs5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671841913,
          "logIndex": 9720345,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "8ec5ad60ad83bb4eda6826aa828272a2d9cd62b9",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3769020955",
      "sha": "8ec5ad60ad83bb4eda6826aa828272a2d9cd62b9"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

