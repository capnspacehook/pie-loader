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
| `latest` | `sha256:95e2c25771a9935b2147e98a98bc68e16005279be1147f444d8a3a6e7006d001`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:95e2c25771a9935b2147e98a98bc68e16005279be1147f444d8a3a6e7006d001) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:95e2c25771a9935b2147e98a98bc68e16005279be1147f444d8a3a6e7006d001"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "93eefdee2386103565e1d32f8950ee33fd68d122",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCLfzdBm4ZbHGO/KSkgzOt+2FjkU6kpQUvZS2b9VJuudwIgJOzHWC1pGUXDthhPBLlupHvQL90DmE7O8Ymq9CBzizA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI0YWM2Y2VjMjhhM2IzNzE0NTYxMWM1ZjVjMTI4Zjk2NjExMjY2MzRlNDJkNGU5MGJjYjU3OTQwY2QxMjcyNTkyIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQlJVeUhqRWpJZ1hzakFsQ3FXK0hkc3ZtdmhTcG5HMkVmMkYzdmtjYlU5UkFpQW9WaFRtbTBaaUhzbk1pbm1Ma05iaHlicnkwSzcyT1NlTXRLSWYyb1owVUE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlIyTjZUMVozZHpsRVRYTjBZbmhUYm5OdU0waElTRWhCTTJ0emQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1hsTlJFRjZUbXBGTTFkb1kwNU5ha2w0VFdwSmVVMUVRVEJPYWtVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZuUkVGbU0xTXhSWE56ZW1KM1RFOUlhMnc1UjJ0NVRrUXJhRVZ1TDFGaVNrVjRkRWdLTlVsa1dsVjFVM3BwVGxaamFUTjFja1JQWnpReVV6ZHhaRUZWWkVJMGJXOXhRbGx0U0RGM2F6QnRPWHBZY0U5Uk1YRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZsYm1zM0NuZzVabE5pV0ZJdmIybHZTR3hJYjJ0RlFuSlNPRUUwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWTk1sWnNXbTFTYkZwVVNYcFBSRmw0VFVSTk1VNXFWbXhOVjFGNlRXMVpORTlVVlhkYVYxVjZDazB5V210T2FtaHJUVlJKZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWTTFGdGJFd0tRVUZCUlVGM1FraE5SVlZEU1VSbFdUWTNWWFpTVUM5NE1XZEtaSEJCUkN0RlZWSkxkVTFOT1RaSlVEVjRMM3BRUmxGb1RYRlBOMVJCYVVWQmQweENiUXBaVEZjd01DOXNjV3czVUhRNGEwVlRZMkZvVTBSbGJVUTBOV2wzUW10Q1l6TkNjVkJ6UldOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2tsS00xUjFXa3gyU25OVmNuaFRkelpwZFZaRGEweHNUbXRPUnpaWGRXNWthbnBhYmk5SUwzb3ZiMnhYVmtGaWVDOUhiaXRHZW10NVVYUkpWbGxSVVRnS1FXcEZRV3RHYmtGSGJURm9VVVZDWkZSdlUyOU1UbXBQWTBaM1RucFBPVTFZVGtoblZIVmpWR2M1UlV4dkwweHVSR0pCVWpGcmRsTlJUblp2VFdOVlRncDFRM0JJQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671669400,
          "logIndex": 9588816,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "93eefdee2386103565e1d32f8950ee33fd68d122",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3753909273",
      "sha": "93eefdee2386103565e1d32f8950ee33fd68d122"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

