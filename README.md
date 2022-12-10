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
| `latest` | `sha256:37fa4ec2c6990e2d0575399f009646181469ccd7d1bfc3bf5d0b4fd6f6ad7f97`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:37fa4ec2c6990e2d0575399f009646181469ccd7d1bfc3bf5d0b4fd6f6ad7f97) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:37fa4ec2c6990e2d0575399f009646181469ccd7d1bfc3bf5d0b4fd6f6ad7f97"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "34ecc61d8acb55737e71b845e1ecb9f30f912f0f",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDJEH5ayUqd6mxYMuMXjT21ldglsvT1o7h6g9zj0Y3npgIhAKyRPq33f5Pyof8nH3P0WEcu8E7kpGSHA6UTrjDp31s5",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzY2Y1ZjdjNmQyZjUyNTY1YjUzZWFkOTU4MWM5ODY0ZTM3N2M4OGFkY2YyNDE3ZjdmMmNlNWYxZmVlZmM4NmI5In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJSHpnWFloS0VGMS9SaDZURm9WeXNEKzMwZVRFT2h5am1tUVZ1WVAvOG5sdUFpQXhQK0h4VnBCMzMvb0JycGl6N0RvRkQrNE1GMS9IQ3NwbVpndHBvdkFRQUE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlJTOXdSVXRGZVhKQlJGbG9UbVozVGtSRmVVTk9TbkozZFRORmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlhkTlJFRjZUa1JKTVZkb1kwNU5ha2w0VFdwRmQwMUVRVEJPUkVreFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVY1TWtwNldFUlJRVWxpZWlzeVpIQkdVVk5XUm5JM1dsZEJjVmxpY0hkeVJteFBPRm9LWmpOVGJtNWhURTFxV1VoU1RHRm5jR05aTW10MU1DOUVNRmwxU1dkM1JVNXdPRk01TTBScE1uZG5jelZwYldwcFNtRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZJYldkWkNtMVFWbXBsUjI1WFpraEJiVFJMUzFrNU1HSTBObGRuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwT1IxWnFXWHBaZUZwRWFHaFpNa2t4VGxSamVrNHlWVE5OVjBrMFRrUldiRTFYVm1wWmFteHRDazE2UW0xUFZFVjVXbXBDYlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVTldSSFdIWUtRVUZCUlVGM1FrZE5SVkZEU1VGd016VmlkekJ2ZUdsVUszUTVabEpvWlUxT09UWnBTMGd4VURZM1NscGpWbGhOTDBKa09URkhNR1ZCYVVKQ01qY3ZSUXBOTkVWeVZHNDNjR3gyWjJaeFZUWXJPWGRhZFhwVldFSXdXRnB2YW1RNU1rUkpNMUJhZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0l3Q2xneU9VdE9TRWs1ZWtGR01TdGlTa3MyU1c1M1lsTjROMEZFY0dSV1ZITTRZVk42VlZKMGRYSjVaa3BQTUN0U1kwRlhLMU5QVGs5aVkwcFZkWFJWWjBNS1RVTTFaMUptUkdkTmJtRm9SVTlLYnpKVGEwZFRiMkZwT1ZKQlEwSmFWMjFxV1c5WlQydEZjakZTYUhKM0sydHJjM1pSZEhoU1VUUkZlalE1WkcxdVZncGxaejA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670632488,
          "logIndex": 8771701,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "34ecc61d8acb55737e71b845e1ecb9f30f912f0f",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3661800835",
      "sha": "34ecc61d8acb55737e71b845e1ecb9f30f912f0f"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

