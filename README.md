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
| `latest` | `sha256:4114428afa24757719fd2be6b1e846bf6641843f8b057dbbf628d964ec90ff67`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4114428afa24757719fd2be6b1e846bf6641843f8b057dbbf628d964ec90ff67) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:4114428afa24757719fd2be6b1e846bf6641843f8b057dbbf628d964ec90ff67"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "28e7eddfffa06ecdbbad179d61c0ab1d84b95729",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIEpTYg5M5rBXzlPMIUK3GguimccxA+6hRdg40Jy4fNDFAiAzTEuKUv2SsvRtZsbmpk/6DRne6xbEXzoVzWN5MlkcNg==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1YTI5MzI0YTIxMTI0NWIzMjZmNWI1Zjk4OWYwZGQ5ZTIwNmQyOWQ0MTY4OGY4MDM1OTQ4MmVlZTAzNDc0MGY2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURzaWNNVmNsN1NVTklGTG9oRW1KSFlOMVRTZUdCbzEwKzFESnhERGdKM0NRSWhBT3FPRnlhd3pVWlhMcEVPV3BwMHNIZ0gxM2NEZUJCQjBRaktPamRuSXZtRyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVldFRkVkamhRZFhKWlYxZFpSMHRGU2tVeUsySldUalUxVWpkRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlRKTlJFRjZUbXBCZDFkb1kwNU5ha2w0VFdwRk1rMUVRVEJPYWtGM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZXUnlzelRTdHRRbGxSY1dveGIweDZVMGRUZVRGcldteFFiRVZTUmxWclZUSllTME1LUW1aUlQwRnVUQ3RhY3pGV2FIWlhTbXRpY0ZFcmNWVkNXVlZyWkcxbVZtNTJRazVVWWxkb1JFSldWalJPUzNwTGRUWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZQU2pSd0NqWXJZM1IxUXpSSlpGcHpjMFZYVjIxcFRXMTZMM2xCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsUFIxVXpXbGRTYTFwdFdtMVpWRUV5V2xkT2ExbHRTbWhhUkVVelQxZFJNazFYVFhkWlYwbDRDbHBFWnpCWmFtc3hUbnBKTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWV1ZjdksyZ0tRVUZCUlVGM1FrZE5SVkZEU1VWc1lUWnViMWQ1YVdKd1JtZGFabXhNWTBaVk9DODJSSFpzVEUxMFNWTk5Oa2hqZURNdmExa3lXSHBCYVVKcFUwWlNXZ3BMWjNjMmRISTBlVkZTVDBoV1FtWXdUbGxFWjJWNmRtRm5WbmxqSzAxbkwyVnVZa2ROZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha0ZrQ20xd2VtWkRhWGh1VTNndllWRnBZMk5vSzIxNlJtWlVLelpNU2taUVJGZFZSRzVaVlRCUFFrZGFWSFJ5VW5WdEwyTklhR2hOVlM5cEt5dEpUWGwyTUVNS1RWRkRUMjlUZG1kMlVsTmxTRXhRWlZSa2NGRmFlRE1yVG5kaGRXcFlURlZVUW1neEwyeGtUelJyVFN0aWNGWmtaemgwYWxadU5GbHpOMjh2ZFdOS1Fnb3hObTg5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671150995,
          "logIndex": 9181329,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "28e7eddfffa06ecdbbad179d61c0ab1d84b95729",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3709158197",
      "sha": "28e7eddfffa06ecdbbad179d61c0ab1d84b95729"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

