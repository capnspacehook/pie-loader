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
| `latest` | `sha256:2c46a4c263be9297e1bd452186a126f68912cf62ea0eb5e8baf5b31e3fe0be5e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2c46a4c263be9297e1bd452186a126f68912cf62ea0eb5e8baf5b31e3fe0be5e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:2c46a4c263be9297e1bd452186a126f68912cf62ea0eb5e8baf5b31e3fe0be5e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "dc08695a0d41a6801f4d46bf86f352d38f46a8da",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDLUdHj7rMV52+eqgUJ1SzYFeO0cGQFCwug4epTErfBlAIgK6B4upRk3y5r0QT+rrlQjYYaLVtpAD79+kkNSaP2CI0=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjNjVmNWI4NDYzNTI5YTU2NzVmNGVkZDc2ZjkyZDEwMTdlM2ZlNDAyMDlhMDg1M2IzMThlYmYxMGFjNjZkYWI5In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQnRERU53MXRwSnlwdWk4RkFPNlZRWldic0xvM1BoeS9RZWpldDhEeUxINUFpRUE5blFsZytIRHprMTV4WWxQUENSQWdqaEZ1R25lU3FZdDVMd0hlSVlrSVRzPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVldFOXVOelJHWlVsc01UZzNTMHB3YzB4M1dsTnNXbFZvZDNKQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlRSTlJFRjZUMVJKTTFkb1kwNU5hazEzVFdwRk5FMUVRVEJQVkVrelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUzSzJwdlduQk9VRkYwUVhGTlNUTnJZblpZVG14b2JEbFBkMU5XZFRkamJtd3dTMGNLVTFWMWRVc3hXSGhYUWpsNVExbHhXRTlHUTI1emJXZEVNa2RtZEZsM056RlVhMDh2V2twUWVqQkdUbXh5U0Zsekt6WlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZCWlRGcUNrTmtNWEZ5WVVORVVsZ3JUVmxYUTJGdVlVVkhRemN3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0WmVrRTBUbXByTVZsVVFtdE9SRVpvVG1wbmQwMVhXVEJhUkZFeVdXMVpORTV0V1hwT1ZFcHJDazE2YUcxT1JGcG9UMGRTYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhYURscFlsY0tRVUZCUlVGM1FrbE5SVmxEU1ZGRVdGWkZRbUpGVHpCU1UyZGxXbFJOUWtJeFpDOHhiazlzUXpKTGVXRkJkRWRVYjBGeVVuWkplbGtyVVVsb1FVeFFLd3A2YXpnMGRYZFBVMVpUZVVKTmF6WXZTbE1yVDNsc2JsUndWVTVUUmt0emNIVXZabWRFWm1aTlRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlJHRjJVMVZSSzNaVFNsWnhjMnRLVFU1dldpOVdaVE5HUW05M1dHRkVhRW8wYXpSeWRqVkllV2QxZW01RWJWa3ZjMFJZYWl0NWJIQkZjbU5FVGlzS2JscDNRMDFJZEdSRmFYbG9OMDByVW14emFVWjFaSFJuTW1aUGVuVjRSRlZwTWs1cllqYzNjamhhUkhNeVlXdFNZMjVtTkVrMWVuWnBha0Z5Ym1Sc01BcFhPSE51VUdjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1676680790,
          "logIndex": 13591354,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "dc08695a0d41a6801f4d46bf86f352d38f46a8da",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4208724047",
      "sha": "dc08695a0d41a6801f4d46bf86f352d38f46a8da"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

