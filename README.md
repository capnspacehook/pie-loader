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
| `latest` | `sha256:dc74e85709d240dac80bab81a3e4b9752f5353b223fc373df2447f590cfba6c8`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:dc74e85709d240dac80bab81a3e4b9752f5353b223fc373df2447f590cfba6c8) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:dc74e85709d240dac80bab81a3e4b9752f5353b223fc373df2447f590cfba6c8"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "a6b9ba59ceb66f9d583aedb15e589611af42b69b",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFw9i27hUKsnARFDnY6v0+PH1ORgRovRD1lnfxKxoNXhAiEA/y37b0M0aMbyEcZrA32TyArV7CxItLipcqJTEP1filQ=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlZGFmYTdlZWQ4YjViZWYxMGYxNDE1M2JiNGViOWZjZDRlNzY0Y2RkNmFhZTFmMjIwMTdlNGYyNmFjMTYzNmE2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJR3FZVlpaSXJEM1pvbFZJdU9XUkJaTUY0VkVCYnJGeHhOeThmZ0JOb1ZqSEFpRUFrN3BzcGJjOXJ4MzBadUFUcE9WV0p5QjhYOXpKUFQvODhPMERuUjV6ckxrPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlQzcHJZVzVTYWpGaFlqbFlRbFZUU21oNlJqQmlURkJEV1dWVmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RKTlJFRjZUbFJSTlZkb1kwNU5ha2w0VFZSSk1rMUVRVEJPVkZFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVVyVGtsWFkzbFdhM0F5WjJGTFRHSkhWMFl2YzNneE5XVnZkVGR3WjNkdmVpOHpia0VLVlZSUFluUTNSQ3RaVFRZNE5EVjRZbGhLUmpoSGFVTlRaelJMUTA1NFRtcFBaWEl4V21kUFVIbEZjSEl6WlZscGF6WlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyUWpSWENrbzNkM2RSWldoSGFtZExSbmN3TVZWRVpqWjJPV0Z6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdoT2JVazFXVzFGTVU5WFRteFphbGt5V21wc2EwNVVaM3BaVjFacldXcEZNVnBVVlRSUFZGbDRDazFYUm0xT1JFcHBUbXBzYVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUZUZoTFZuUUtRVUZCUlVGM1FrZE5SVkZEU1VORFNXbHdNMngxTUdwRVVHVkVaRlpWVGxSdVRscHJVRkZpVERsNE9XRmhOalJ6VFZWdWVYaG1NRXRCYVVGUFIwMWxSQXBCUjFGYVVHVjZSRkpVY1haNFMyeDBOM1E0UW10VFkwNWFUSE5ZY2tvdmVYUmlha0pvUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ2pacFVYSnRjR0Y1TUdZNWRHZGFWVnBuV1VrclJGRmpjSEppVkVOT1ZVRXZaMnBzTlZsRGR6VlZiMHc0ZW1KTU1ETkhZek5KYXpOTk9FSlVkbkI1TlRFS1FXcEZRUzlIY2tsUVdtVkJRVTQ0V1RaeWNuWlRZWFZqYUhSM04wUTVNWEprTVNzclRHWjJaVU56Vm13cmQxSllOR2xLYVRWRGRub3JZV1EyTlZsMU1BcEllbkpsQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669422973,
          "logIndex": 7858278,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "a6b9ba59ceb66f9d583aedb15e589611af42b69b",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3551474797",
      "sha": "a6b9ba59ceb66f9d583aedb15e589611af42b69b"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

