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
| `latest` | `sha256:dc5d3db473cedbdcdbee0c5e05a78b01d53d84d617a87589ce21917355042287`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:dc5d3db473cedbdcdbee0c5e05a78b01d53d84d617a87589ce21917355042287) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:dc5d3db473cedbdcdbee0c5e05a78b01d53d84d617a87589ce21917355042287"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7b5679e690e67f90367bb1ad3cc35284df42834c",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFDZv4CeaSHhStA8D28WdM85YZOj1CMLX/B6Brdy+efpAiEAy4jHL+gAlc6QEJeuhoYUTMRFQ4qbhmtqr10H/oZ8lEU=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwNGI5M2ViZTgyZTkxYmQ2MzQ4ZmMyYzU3YzI2ZDFjM2U4YjZiMWUyYjkxMGRjNzNmY2ExMTdjZjg0NDk0OGRlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNueFVKb0xZN2tVSU5HMU9UMi92bGZvNmJjMEdIcktxR2xrS3FzTUM5V1V3SWdlTXREODhkWS9mYnRRQUJES3pJajZYejJQaW1nK3lqVG9iajFpRHVrSmRVPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlFUWmxTR1JUWjFGMFJuTmhWMWhNYzJ0R1NubzRTa3RqYlRWemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlhwTlJFRXdUVVJGZDFkb1kwNU5ha2w0VFdwRmVrMUVRVEZOUkVWM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZYUjFkd1RYbFhXblZEYjNReFlqRldNR3hVTWxrNEsybEhRa2RGU1ZaS05FTk1WRGNLY0ZwVWVERXdPVTkzUm5OSU1IaHBLM3ByTHl0TloyaHNaREk1TUdKTWExcHBOVFUxV0RZM04yVXlPUzlGWTNoUmVHRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZCU1VKWkNtbEhTVTV5VlhSSVNWWkZZbkowYTBoRWVrcEdSR1puZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOWmFsVXlUbnBzYkU1cWEzZGFWRmt6V21wcmQwMTZXVE5aYlVsNFdWZFJlbGt5VFhwT1ZFazBDazVIVW0xT1JFazBUWHBTYWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWU1RkTWMwd0tRVUZCUlVGM1FrZE5SVkZEU1VWd1FYZHhTWEJLT0dOeVdVUjBLMWxtYkc5NloxWkhVVkp4YVcxamNXSXZMM0Z2TW5oUGJqUlZVMHRCYVVKdmVIbzJLd3A2YjBwblYwYzJTU3N5TkdNck1FNUpVRmMyYTFKTFdHRnVMME12TUVReU5UTnBZbk5sUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ25aUlJXTlhjMlJKU0VKTloxQmlUamRKWWpCblZETm9NRWhOYTBwT2RUSjRUV3hEWmtWMFJVSTJNa0Y1WTNoQ0sxWlFWbkY2UVVoVU1DOHZRbE0zTVVzS1FXcEZRVEZNTkZrMVprbHlVVVZHTkd0NlN6WlJXbkJTVkZCclFVdGpWa0ZuYjFwNlNsSnFaMW8zYjBVNVJERkljeTlKVjFCSmJqQllZbXBVV25oRGRBcGphVkJyQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670892040,
          "logIndex": 8966748,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7b5679e690e67f90367bb1ad3cc35284df42834c",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3681112490",
      "sha": "7b5679e690e67f90367bb1ad3cc35284df42834c"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

