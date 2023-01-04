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
| `latest` | `sha256:38401ee91d9c87d5d3b4ad90e9391881964f3fbfa5aed9b1e1eb5c977766bc81`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:38401ee91d9c87d5d3b4ad90e9391881964f3fbfa5aed9b1e1eb5c977766bc81) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:38401ee91d9c87d5d3b4ad90e9391881964f3fbfa5aed9b1e1eb5c977766bc81"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c864ee29dae4bf512c93d1365f690439ccc4cca9",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIDSpQ/srYSrgnosXARWAP2Lt8urHYPoh9rrkskilrnI7AiEA79GyrnnYGWEhS6QxMHp8bxbLRgU9H5Q1AV/mq6Jc8GQ=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhNGI2NDU0NjdhNzBkMzUyMmNmNzVmODViOWYxYTliNDA4MDExYTM4NGVhMzRkNGZjNGVjNDY2MWU1OWYwODRjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRC9IWTdPdFkzaVRoZi9GMWM1eUxQbTBiSmhySEN6VzQ2VlRPMzhzaTVMYUFpQjQvTjhpaXo3LzA4em9ocExQeG80bisrSStYd3RQaGNzdy9uVGh0MzQyenc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCaFowRjNTVUpCWjBsVlpUQTRWREZZUlROeGNIZHpXamR0YzNoVmNWWlZiSFp6UWtWamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVRCTlJFRjZUbFJWZWxkb1kwNU5hazEzVFZSQk1FMUVRVEJPVkZWNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZYU1cwNGFUQnZZa2g2VHpoRGRERk9aMkpoUWs5YU1FWkpWbWd4YzJwWlptUnplSFFLYTFoSk5GZ3pZMDVLVGpOT1dIbGFiMHBqWW5ocFZtOXdObFZzUTA1Tk9YTXhRVVp4YmtoSFJrOW9ZbnB3ZVU4clprdFBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV5ZFRGbUNsaFBXV1JyTlhoNlVHbHBSbFpEYTJaR1JVeDRTamxSZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwUFJGa3dXbGRWZVU5WFVtaGFWRkpwV21wVmVFMXRUVFZOTWxGNFRYcFpNVnBxV1RWTlJGRjZDazlYVG1wWmVsSnFXVEpGTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXTms1TWFYY0tRVUZCUlVGM1FrbE5SVmxEU1ZGRVdYQjJhelppY0VkVldrdEpNbFJIUkhCRmNVdHJhbTlwZDBsdmVYaHRXV2xQVmtRM1lUUkdkV2xRVVVsb1FVcFdNUXBWVHpac0wxaEhXa1ZXTnpSdlNuaDNTaXRaTTBkWFluUk9kVk5SVGxoRVQwUTJSVXBpWjJ4RFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVkwRk5SMUZEQ2sxSFIxYzFTbTF1U0hCTkwxaFVSMWxET0VsRFUxZExRbFJKUVd4MEx6bDFTbkprWTBzM1lVVm5Walp3U0hWVWFEUkVaMWxFZW1OTFYyaEhhMWd3WWxBS05VRkpkMGc0WTBKb01UQjNaWGhGWld3NGVXOXNLMDFvZVZwdk5GWldLMmRrVkcwcmVGaHFiRlJXVFdGSlRUWkZUR3RKVXpZclRIVndTR3RXV1dOb2VRcHpjVkJQQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1672792579,
          "logIndex": 10424855,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c864ee29dae4bf512c93d1365f690439ccc4cca9",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3834135830",
      "sha": "c864ee29dae4bf512c93d1365f690439ccc4cca9"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

