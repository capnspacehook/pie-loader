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
| `latest` | `sha256:9358e2f3130186f1f99208a07ce042b506a7385674ab611822ab8298258243bb`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:9358e2f3130186f1f99208a07ce042b506a7385674ab611822ab8298258243bb) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:9358e2f3130186f1f99208a07ce042b506a7385674ab611822ab8298258243bb"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4b15d3f270bc35a4edcead1c80fee0b1858df5a3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIGnGNkQimxlrXHNnKfcszLt0036WPjGNxFfgghgS/VjVAiB7Hb4ia1R9QwVnsG3quPcf4mhIiG4D7bPqRGduFNPfgg==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5NmRjY2QyMDQzNGE3NDg0NmE1ODhmZDVjOWRkNzJjZjE1MWE3MTdmNzJjOTFiNmM0YmNiNGM4NzNjZjk1MWVlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQ2QrQWxqNkJON0xicTJ5VzlqNFVpNmhUc2VJMjVKbjJQMTJyUW1oY01MWEFpRUErOE5rRGVDWERrakZLSXdtVXBkQmx5RFBMdFAyZWh2Ry82Qk1oMjdpWEdzPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlZIaHRWeTkzTlZOSFpGSnRWMjlFUTJsM1JsZ3pkRlZ0VVhZMGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlRWTlJFRjZUMFJOTTFkb1kwNU5hazEzVFZSRk5VMUVRVEJQUkUwelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUxV2tORWJXMTZWbVJEWkdsS2VGcHZLMVY2ZUZSdWRFcFZlR3hHV0hOQlRubHZkM1lLTDJoTk5WVjZUbkpKTkZjdlYxUnNSVGhwV1RoM1dVazBZVTFVVkdWUmFXZDBRU3RqZURaSVJDdDJObTFpY2tWdlMzRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZCTDBORkNtaHhhVGhrY2s4NFFWa3ZWV0Z1YnpoalUzVmFRV3huZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCWmFrVXhXa1JPYlUxcVkzZFpiVTE2VGxkRk1GcFhVbXBhVjBaclRWZE5ORTFIV214YVZFSnBDazFVWnpGUFIxSnRUbGRGZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZU0dSd01FRUtRVUZCUlVGM1FraE5SVlZEU1VSb2FrTnlOWEZzYTBWUlZsbzBRMk5WZVdSc1kzcEtkakJ0WVRaUFVrbE9jV2haU1VwWmJEVlJOM1pCYVVWQk5rcHlVQXA1V1ZnMlNtWnJaMlZsU200NE1qWkpiRVZoVldSM2IxUjFhako1YzFsSU1EQndPRmRWVTJ0M1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2tsUlozTTNWRVJ0WmpKdVlVdDJjVUpQVjJweWRtcEhWMjVNY1dWMWJYRnZRakJKTVcwMFNqVTRTemRVU21sdVEyUjNWbkJ6T1hFdlowTnFOVGxvTW5rS1FXcEZRVGxTYVV4RVFXMXFOMUZMZVdOblExUnFUWFZDZG1jeFIwOW1Memw2V213ek5VRmxiRWc1Y2tSbEsyOUNUbEo2TUZaS2IydDFVRU5CUkZwS1NncFVlblF5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674088740,
          "logIndex": 11477566,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "4b15d3f270bc35a4edcead1c80fee0b1858df5a3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3954200169",
      "sha": "4b15d3f270bc35a4edcead1c80fee0b1858df5a3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

