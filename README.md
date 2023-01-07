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
| `latest` | `sha256:64c92be6b0513359bf0a0bd8a5e2807286a3bd65143d3f45369e4fb5b426d158`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:64c92be6b0513359bf0a0bd8a5e2807286a3bd65143d3f45369e4fb5b426d158) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:64c92be6b0513359bf0a0bd8a5e2807286a3bd65143d3f45369e4fb5b426d158"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f660d0cee04a650d6e8382ccb5ad6664328a7d1d",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIDW8fra56SnpQ1ugYjSXEoGEnUmfAYv67u9tWQgoKIgDAiEA2nRVZlrD5zGU6smQrXXyRsb9nOaypun77bgBdAQ66k4=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlMzY5MGM5NDY3MmQzMDlhNTM0YjFmZDYwY2YxMTAzYmU3MjhhN2VkYzk0M2IzOTI0NmViYzI2MTJiMWQ1ZGMwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRDUyTGdWWlE1TjJVdjRha1RNR0JxQ1BlWk5GOEN0ZWZEU1lFM3FNQzJDeUFpRUFnUGEzekdXVDBlblBFTCtEeFJxanFCUU9xdUZZR0ViUG1Sd2dwSnRPYVg4PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlFYaEhOMGhTUW1sS1N6bHdSVVphTW5oMmVVbzFVamRoUTJkRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVROTlJFRjZUbXBOZDFkb1kwNU5hazEzVFZSQk0wMUVRVEJPYWsxM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ0VG1SR2RsQm9aRXhqUVhwS05EaGhUWFp6UkZONmRtNTRZblpzU2pSSlJDdEdRbklLUVhwV1MydFJNM3BoSzFSQk16aG1RbU14VVZSTU5sQTNWMVUwT1VwUFZuRmxibUZCVVRsdE1rRkNaRGMzZVU5bVV6WlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZDVjNwQkNrRmhNVTl1YkhOQ2FrMTJTemRwYURGWmRtSjJTVk0wZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxT2FsbDNXa1JDYWxwWFZYZE9SMFV5VGxSQ2EwNXRWVFJOZW1kNVdUSk9hVTVYUm10T2Fsa3lDazVFVFhsUFIwVXpXa1JHYTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYU25GR05Fc0tRVUZCUlVGM1FrZE5SVkZEU1VWUldUY3dXbWRYZEhaWk56UjZjRGRTZVc4d2RtdzBVWGxLVm5GRk0wYzNlbXBuTUZoMWRHbFJLMjVCYVVKMmNrRmlhd3BUUzB0Qk5XZE9SRTVIY2psalowcEVUVmhSVG5OblUxVTFRbmNyYURSVFVIRnZRV3A2UkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ21oMlFXTlVkMjFyT1dWcGJFRnhTSGR6VjNObWMyNVpTbXRoY2xVclVFTTBPWEJhTms0MFIxTlpjbEV5TVVoME4yb3laR2R2U0dKamQzTmpWbXhPZVVjS1FXcEZRUzlpVUd0VE5tTjNSSEZzV1hsVlVWRkNRMXBtU25wSmREWnRWV2hpTUM5YVNESlZjVXB0VWs5YVpYVk1lV2hLVW1WME5qZFdVRTE1TDNCa1ZncHpVWFpMQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673051813,
          "logIndex": 10635616,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f660d0cee04a650d6e8382ccb5ad6664328a7d1d",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3859574931",
      "sha": "f660d0cee04a650d6e8382ccb5ad6664328a7d1d"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

