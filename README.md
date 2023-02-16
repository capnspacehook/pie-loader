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
| `latest` | `sha256:6244351290e97e8d7ebc5223880611556533ae996fdbca2b68c12184b1f20adf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6244351290e97e8d7ebc5223880611556533ae996fdbca2b68c12184b1f20adf) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:6244351290e97e8d7ebc5223880611556533ae996fdbca2b68c12184b1f20adf"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "11c414666c7c780ad56405851e4fb9e538518a21",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDZR+NwWWeXrGjv+oja1ypyuAKVgJX+q9JNfrNlKmFxFQIhAJhQM5Mrub9b+svA2vmklXqBmHxGMXKVB+K0BxfBbV+f",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiY2ZiY2YxOGM4ODI0ZjFkNmM2YzM1ODRiODZkODA2NTA2Y2ViMWUzYzNlODM1ZDM2YjY3OGYwMjA1NDczOTgzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUN1ZnFLM041TGxGVXVWSEhJa3ZTQUlDYzVJSWxSd2ZlZUx0bFltdGYya3JRSWhBS2UvSW9lY1d2Mmhqc2V0QnhXTjR2V1VUUStRK2U5VXc4TGgxcGYyVlcvbyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVldWUnVObVp5TWxWRWNscFBZMFIzYW5OelVrcDVNbkZaWkRoSmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlRKTlJFRjZUMVJWTVZkb1kwNU5hazEzVFdwRk1rMUVRVEJQVkZVeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUwUWpOTGNuTmpUbGhZY25wQk0xWlJlSEJZVm5CTk5tcDRVVmRqV25CM1lraExWU3NLVFRkRlRsSjJSRFExYlVOMU9GSjVTaTl5SzNGbVVYZFJXRkJQTm5vMFRWbFpVM2xLVmpCdU5IcGhNbmxtZDIxdE56WlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzYzFCWUNtVjZXRzV2YkZrdmNETXpiVTlSTUhaeGNtRlNPWE13ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoTlYwMHdUVlJSTWs1cVdtcE9NazB6VDBSQ2FGcEVWVEpPUkVFeFQwUlZlRnBVVW0xWmFteHNDazVVVFRST1ZFVTBXVlJKZUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhV0hGa09Hb0tRVUZCUlVGM1FraE5SVlZEU1VWVVRFNHZURlJZYUdoclUwMHhkR05hU1VWNWFYWnRLM1ZDT1hKNlpXcGpiVWhoVGpoVFNHVXpVWE5CYVVWQk1tTTVUQXBPV0M5NWVVeFJZV3Q1U0RFNVVFbHVTWFYzZEhsSlowWTROemQ2ZGxSRmJDOVBRbFZyUnpSM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGSmFuRmFTR0ZCUWxodGVEWmFORWM0TTBrM1ZHbFRjRlJtWlhoS2J6TnpTbEk0UXk4dlpGVkphR1ozTm5sc0sxa3JXRUpzWmpWR1pXOTBUMGhNT0hBS1YwRkpkMGRJYkdkeVJFa3lWVlZ4YlhOR01HWnRTMVZVUVZkeWNsRnhWVWx0VVdORlJsSlVjM0JpVkdGNllVOVRkbFY1WWxNMVZsZDFMMjlNVFd0dmJnbzRVRkZMQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676508018,
          "logIndex": 13438674,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "11c414666c7c780ad56405851e4fb9e538518a21",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4189489955",
      "sha": "11c414666c7c780ad56405851e4fb9e538518a21"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

