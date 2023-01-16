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
| `latest` | `sha256:ca144c93f908a2f46cb287338841920359c23c34a28f870f6dfa168ab993e4cc`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ca144c93f908a2f46cb287338841920359c23c34a28f870f6dfa168ab993e4cc) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:ca144c93f908a2f46cb287338841920359c23c34a28f870f6dfa168ab993e4cc"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "dfac1bee6b9455d467359c96163c18b1fdcfb3b7",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIH4+ZJxpLzM619k9nTl0a/cYv4lhN6NdaIDIm3cQHExSAiEAl4zjXuW0eAX/7Lv4E1vgvuVeEbJ9VmKx87MM6CawVog=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5NzRkOTAwNWY3YTA1ZjNlNmNhM2ZmMzA3MWQwMmExMmVjZmQ0NDE2NGU0YmY2OGVlMTg1OGY1NWU5NGEyNGJlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNuc0pFRWNVVytQMWt4Y1FnekxkeUpja04zWHNLNmpMQ3RZUmNmSGpUT2tBSWhBUGpteVJmWGdJTklFL0ozRXQzd3FNTVArdjZiOGtOQnB1UE5VeGZSbWtKciIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNWRU5EUVRCaFowRjNTVUpCWjBsVlRVTjNNa3hLV1dsbUt6bEdVVk5rWWtsaFYzVlZXV0pwTld3MGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlRKTlJFRjZUbnBOTTFkb1kwNU5hazEzVFZSRk1rMUVRVEJPZWswelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ1UlZkSFowOWFZMjVaT0hOS2NYVnZUREZ4U21SQ09YTjBabm81T0d4bU9WRmpXWFFLUTBaWVVDdDRRa3MxTUZOYU9YZE1VVWRSUVdSSVRHNDBWV28zWjJGTlFVMHZkR3BLWW1KMVRYbGlWREF2YkU5Tk1uRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV6TDJoSENqUXlZVzR3WkVKdmNYazFZM2Q2Y1RFMGEyWm9aelJGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0YWJVWnFUVmRLYkZwVVdtbFBWRkV4VGxkUk1FNXFZM3BPVkd4cVQxUlplRTVxVG1wTlZHaHBDazFYV210Wk1scHBUVEpKTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYTkVGd2VXUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRWQxaGhTMWQ2YUdodWRuVkNhMGN3U2pGNmRXUjVNSGwyWjFwQmFFbGpaMGhTTWtONFQwRk9RVXh0ZDBsb1FVbFNRd3BNVDFGNFZEbElTVFpsV1VGT1RHNUlhVGx6ZUVab2VHdHZhR0pVVEdaTFNuVnlSa294ZEc1SVRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeWEwRk5SMWxEQ2sxUlExbDBWVVJHTjFBMlQxWlNkVFp4VUZadWJrVXpaRk5EYjJzeWMzZGxjbXN2Vm5Cdk1EWlRVemhyWVhWd1N6a3ZZMFpqUWpGMGFtSXdWRWxCWm5RS2RqaEpRMDFSUTNwVk5XSlVRVWgxVkV0d1QwSmliRmhaTjJGNVQyeGtRemx1Tm5kMk5rd3dNM1V2YkRWRmNUbDZTbGxpZW1oSFdFSm1PVXdyUzJ0V01BcFpUMHR5Y2t0VlBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1673829487,
          "logIndex": 11256323,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "dfac1bee6b9455d467359c96163c18b1fdcfb3b7",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3926067029",
      "sha": "dfac1bee6b9455d467359c96163c18b1fdcfb3b7"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

