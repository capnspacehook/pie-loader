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
| `latest` | `sha256:cf695989ba7791d3d143e554fa5ec7ed43ce4bb33b7c7163666ebb8a5b83f27f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:cf695989ba7791d3d143e554fa5ec7ed43ce4bb33b7c7163666ebb8a5b83f27f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:cf695989ba7791d3d143e554fa5ec7ed43ce4bb33b7c7163666ebb8a5b83f27f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "1f105c361ae91e3233b369b81b24ed498040d0fe",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQClsx0SXnDPRyQAQxxovXcNe75tV6SRUB1E9Iq7rfgHYQIhAOtLscPcfPPqsCCa1N8vmDpltRoROHkx+0qR9zgGRC5l",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5YmExMWIzMDc3ZjBkYjdlOGY5ZGU0MWZlNGNhN2NkZTQ4OWYzNDIyMGE5MzEzODFhYThkYTUyNTFhYmU0YTIwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQ2pZUDI5NG1iUHp6VXljK2xMSEFKMzk3TFRGYitjbzhwTlRRazREODlZekFpQkczLzVLUW1pdkNyb3c0WVB2STR4SVhHbG1mK0xlUzBXR0FWQnpJOU5RREE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlpFTTBlRVJsVEdNd1duTkRWR0lyT1RGMmNFSlFVME01VWxadmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVhwTlJFRjZUMVJWTTFkb1kwNU5hazEzVFdwQmVrMUVRVEJQVkZVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZIVm1vMFJHRkxUREJEZHpodUwySlRRWFZtYVVoSVdtbEhhazVuWm1kUGFGWXZXSFVLVGpad1VubEllazk0VUhvMWJuWTNOM2R6TWtJeGVETm1iVEphUzJGSlNrYzVlblJIVTFnMmMyeHBUREJaV21oSWRIRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZpWmtOckNrOUNkMEl3TkdWa1VIVktVRzFKZFZocFdFVnVTa013ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoYWFrVjNUbGROZWs1cVJtaGFWR3Q0V2xSTmVVMTZUbWxOZWxrMVdXcG5lRmxxU1RCYVYxRXdDazlVWjNkT1JFSnJUVWRhYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaVlhSNmNXOEtRVUZCUlVGM1FraE5SVlZEU1ZGRE1tTjZPR2hzZGtsMWFqSjFOMGw0YWpGVlZWSk1iM0pqVm5oNmNYVXdXR0ppT0ZObldrNURVbWRSUVVsblZ6RnhhUXB1U0VSTFkwRkNlVlJpZEUxTmVIWTNNMVJTUXpSbVNXMUxTV3BYVVZKSU1rdHFlVW8yV1dkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2xodGFUUmlNRUUzVEVVMFpDdDZaVTVDZFV0cmJtdExSU3R1ZDAwMllXdFNSMWQ1ZWpGYWFWTkRZbmxIWVdJME5XcEdZVEJTUjJoMFRqVkNXR1E0TDIwS1FXcEZRV3hsYzNsbWVsRmtZVzlsVW5kM1dWRnVTVUkwU1N0c1pGSnRiRXd2YVhscmJGaHNMMDFDV0daTFdXYzFNMFpwY2xORWRVRlBiWFpHTkd4SVR3bzBiVmhxQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675384820,
          "logIndex": 12510610,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "1f105c361ae91e3233b369b81b24ed498040d0fe",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4079970794",
      "sha": "1f105c361ae91e3233b369b81b24ed498040d0fe"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

