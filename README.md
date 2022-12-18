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
| `latest` | `sha256:5804426f682c526451c06de9070f9aa44fe2d2ac4db824fd34eec606933c8e5f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5804426f682c526451c06de9070f9aa44fe2d2ac4db824fd34eec606933c8e5f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:5804426f682c526451c06de9070f9aa44fe2d2ac4db824fd34eec606933c8e5f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "0bf1a5c068d668978d32b84ae4e766f52507f5f4",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDczgW2A6P8rDL2PrF2duy3AOGucJVTC/QA4PJ7NgEn+AIgYDqnqkrBzdODM1GCC4LMmAd1MEqWRhKi9VWPKjOgO8w=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5MDI3OTM4NDIwYTUwNjFmYzk4ZGVhMzRlOWU4Mzc1MWZjZTI5OTQ2OWFkMWNmMTdlNzQzMjJhNWJiNDg2OThhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRnZvOHBxeFRDUXplcHRiU2ZwZHpFd0JqZ2lrTWhnaWZsQmpjVTBjeVZ0VEFpRUFqS1RFTENZWkxTUjByeXE4cjk3WGg5T1Z5dUVGbTJ2TUxFR1p2RkdycDBrPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlFUQXlPV2t4YTFOV01HWjNOR2QzYm1sb1dVVndWbUo0ZERnd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlRSTlJFRjZUbFJGTlZkb1kwNU5ha2w0VFdwRk5FMUVRVEJPVkVVMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZoVjJaYVMyOUxTM05oTlU5V1NIcHRkSEE1TVV4TldERXdiSG81YzFOSFN6UXplVlFLTW5ZeVNYVXdieTloYTNOVmMwdHNVblZSVGtwMGNGSk1jbkF6ZUVkblQxazNNa2hPVDA1RGQxVkhOSEJrWlhsdVNqWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZvTUVwTkNuRkNkVlkxZFd4U2FrWnZlRUZ2ZW1OTFZFWjFkR0Z6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkWmJWbDRXVlJXYWsxRVdUUmFSRmt5VDBSck0wOUhVWHBOYlVrMFRrZEdiRTVIVlROT2FscHRDazVVU1RGTlJHUnRUbGRaTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWYVhGQ1pHd0tRVUZCUlVGM1FraE5SVlZEU1ZGRFRuUlNiR2R3V25Gc2ExSnhSMFl5TmxSVFYzWjBSazFoYTNkV2FtVmtNbVkyTUVWelFqZGhkMWhuZDBsblExZzFOQXB1WW5JMU1YcE9OakJ4ZG5SYUx5OVRSSGg0ZDB4U1FubzBlblJwTlVvelVqazVhM2RSTTNOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2tsV05uWjVPV3d6YVVWeFJsTjVOazFWZVVONmJqUlVTelVyT1RKRE1YaHhMMHcyV21aeWVrbFRZV1JTTlcxR1FWTlhWMm96Tm5CR2JIY3pRVFZqVkdNS1FXcENRV1JrZUU0emJXcEVSRnB2ZW1WaE1IbHpWazF2UVZoTU9ITlNabmxTZG1wR2QwNVdkbUppYmpJcmNGRlJTRXRYTXpWaFZVbGpWbGxTVTFsbmJncERUSE05Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671323751,
          "logIndex": 9312063,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "0bf1a5c068d668978d32b84ae4e766f52507f5f4",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3722475053",
      "sha": "0bf1a5c068d668978d32b84ae4e766f52507f5f4"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

