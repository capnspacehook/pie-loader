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
| `latest` | `sha256:a422fba3a569271d7793a6db5696c9e82135f439df0056436ec79bf662be0d14`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a422fba3a569271d7793a6db5696c9e82135f439df0056436ec79bf662be0d14) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a422fba3a569271d7793a6db5696c9e82135f439df0056436ec79bf662be0d14"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "24c8f4fb0219d7927bb083a858f233e73487aa68",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQD75kfXyEj8vWnKzJOnq5K3QKuHdOSveH68L8TxJjS8AwIgelcml5gJBn0LVinO1L2PlpWQKFmdhgmp3Phlh9IMRZA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1NGRhYzM1Njc4NjUwNjQ0ZjUyYzZiMjE5ZDY2MmE0MzRhZTJkOGJlMjQyOTg1NjUyNDFmOWJhYmFhNzBkY2MxIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUR6QTJQMThtWmxtZU4wN1FpMk1CUGx3enZnV0NPTE1UTXFObU05M08vZzN3SWdRNVJMY3JyK0pCdGdXY2kvai9oUVNJK0ZRNndTdzB3blhHMXIzQmJIaVU4PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlRUUnpSVGh3Ymt4eEt6UkxOV05hVEc4cmRFWTBUM0I0U1d0emQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlhkTlJFRXdUVVJSTkZkb1kwNU5hazEzVFdwRmQwMUVRVEZOUkZFMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV4YkZSRVl5c3JNR3B3WmxSNVJ5OTJlazVqU0NzdmVHOVFOREF6TUdoT1drcFNkazRLWmsxYU1EZEVUMUpsZW5KSWJGVjRUMHBWUmxkdU9ESkRZMFp1WWpWRVowUkljbXhyYURFdlFsSlhlVkV2VURkMWVtRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYwUm1Vd0NrcEJTbW8yWm0xWVUydDFTM0JxY0U1YU5qRldUVGhSZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsT1IwMDBXbXBTYlZscVFYbE5WR3hyVG5wcmVVNHlTbWxOUkdkNldWUm5NVTlIV1hsTmVrNXNDazU2VFRCUFJHUm9XVlJaTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaTkhoSlRWRUtRVUZCUlVGM1FrZE5SVkZEU1VSTkwyMUVObU14UlhCUGVFZHJPRVZ0ZDIxSlUyaEpSR3RzTUZaNWQwSlVhVTVxVVROV056YzNNa2RCYVVGTVowUlZTQXBpT0hOMllYSmpNRzU2Tm1zeFdteEZSa0V5WVVwVWNXbGlXbk5XVWxObmJrcFFjM05DZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0ZaQ2tGd2VEVnJaVkpLYjJ0dWRqRkliekJ4WkZaM1pEQkdTRFowZFRrdlExb3laaloxYlhBMVlqaHNNMEZ4UVRsSWRWaHRVVTh6VFVjeVpsZFhTalF6WTBNS1RVYzNZbmxTUmxKck1YazJZV1JpYlhoelYwNXRhMFZEZEhoM1NFODFaMDQ1U1V3MWFrb3lhbGRQTlZwWlFqaHhPV05pYzB0YWMzaEhSemczTkZSSmJnb3JaejA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675989670,
          "logIndex": 13010279,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "24c8f4fb0219d7927bb083a858f233e73487aa68",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4139715685",
      "sha": "24c8f4fb0219d7927bb083a858f233e73487aa68"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

