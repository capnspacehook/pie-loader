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
| `latest` | `sha256:388ba77e40d844c7f9c97cfcde2db09ae83ffb04c42ed3461e98da88896b4f4f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:388ba77e40d844c7f9c97cfcde2db09ae83ffb04c42ed3461e98da88896b4f4f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:388ba77e40d844c7f9c97cfcde2db09ae83ffb04c42ed3461e98da88896b4f4f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "db150f073c9c707bebdc92e344471cf6ef286c8a",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQC4RGRHFdY9IU9AyB0iLuXMsNC5lPfTe0OL9hN/+beG+AIgdjvS9PetZVPZvRPFKJVoywScfImpKTyMgdMrZfK+R/w=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5YWJjMjZmYjk3ZjNkMjgwYzFlMmQ3MGQ2YzViY2M1YjEwM2ExZTcxOTczOTJjM2RmZGYyMDIwMWJjNWQ3MzQ3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQXBZVWR3UFBJVXFXazhaaWk2YVF3MWMxUFh5NGh0dVhvakxmL2pOeHdhR0FpQkFGcXNHYVRJYXlTTjlldDYxUlVxLzVZeG5YNDlYa3lTN1dGK1c3dnZuWkE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlZ6bGxTVXBKVkdGTFNFTnRVVGxUZFM5dldscGlRMGN5WlVSdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlRGTlJFRXdUVVJOTTFkb1kwNU5hazEzVFZSRk1VMUVRVEZOUkUwelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZoVWtjeFlrc3dhaTg0UVVGcWRIbHBjR3R6YVZSTVlreERPV012U3l0aFRsVnBLMHNLY2pCRmRWcExOR1JSYUhGTVQwOTVPRlJaWjAwck4zUmxUbmx5YUZWaU0ySlZWV1J3Wm1oNlVuRkZSbVZUWW5sUVkwdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ1VkdwWkNuTk5jbFEyWmxadlNVZ3dRVmxTYUhsU1NVdFJSME5GZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0WmFrVXhUVWRaZDA1NlRtcFBWMDB6VFVSa2FWcFhTbXRaZW10NVdsUk5NRTVFVVROTlYwNXRDazV0Vm0xTmFtY3lXWHBvYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYZVROMkt6Z0tRVUZCUlVGM1FrZE5SVkZEU1VGV2JWWkZTVTFrV2l0cFRuRTBiRkpwV1dGdVVUTldXbFJ3WkRGME4zTnZRakZYZGpSRFptaEhhVkZCYVVKSlRXeFdRZ3BMV0hCMk9HOVZTVlZ0UnprM1F6RTBaRVpaY0VscFlWQnNNU3R6VkRkNk5qRmtVVFJIYWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha0pHQ25CdGJsbE5OM3BWYzB3MlFTOTNhMjlvWXpoUUwwdFViVkJzTXpOdVkwaDZZMUZVTjFkRWVsaGlNRXQ1TVd0a2EyUldNWFEyY0RNM2VVZE1RbEE1YTBNS1RWRkRVWEJQYzNOSk1FSnFUa016U1dSVWNtNUtTUzkyTVRGMlRXMHllR013WW5BelUzaFZPR3RGWkZWbFZrMHJVbmNyUW1vM2RtWXhjVWRFYmpjNWNBcFdObmM5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673743268,
          "logIndex": 11194754,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "db150f073c9c707bebdc92e344471cf6ef286c8a",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3921003283",
      "sha": "db150f073c9c707bebdc92e344471cf6ef286c8a"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

