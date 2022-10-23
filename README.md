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
| `latest` | `sha256:d3129f59f7f49ac101afda9aa63f3582c29c39cfb47000361860f223a802133e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:d3129f59f7f49ac101afda9aa63f3582c29c39cfb47000361860f223a802133e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:d3129f59f7f49ac101afda9aa63f3582c29c39cfb47000361860f223a802133e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "90e7b30a96c22c390c339676d9880c85c1e88342",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQC94O0GZLI25GaKwCZvVktwcWdkGytEtgAJM9A8Lg3zaAIhAOYUTZFoIm8l5W2jmpLyQRBkourwIWB92EP13z2kawIY",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5Y2QwNDNlMzUzN2Y3MzM4MTRlNGIyNzExOWI0OTBmYzUwNjI1NGE4MTUzZmNlOTNkNWFmNjBlYTNlYWQ4N2YyIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURFaUYwcUtMcTNLaER6Wm9yZ0hFQXFkU2NGKzdMZkxNQjhlcUlaOW03VWpnSWhBSkpuTzRyeEl0WkFKYUtTMm1ZTWVueTVZeEtuVXJTNDhPVHlST2ZOTVovSCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCaFowRjNTVUpCWjBsVlJHMXBjR3RDVmpCSFREbExWMGhMY1N0TVRWWnJaRzlRVlRsWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1hwTlJFRXhUbXBWZWxkb1kwNU5ha2w0VFVSSmVrMUVSWGRPYWxWNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVU1UWtGcVZUSnVSbUZrWm10WWJISndSblZyUjB3MWFISjRWSFp0Y1VONlZHUmpRblFLY0UxU1RWaHlTa0pZZDB0SU1Fa3lZeTlPVkRkSFJVWnZka0phWVhZekszVk5RMHBLTDA5WU1rNWpOemx1SzFsc016WlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY0Y1c5VUNuZGpLMnRFWVdaMlJVTm1UbWwzTjJSR1QxcGpNRkl3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWTlIxVXpXV3BOZDFsVWF6Slpla2w1V1hwTk5VMUhUWHBOZW1zeVRucGFhMDlVWnpSTlIwMDBDazVYVFhoYVZHYzBUWHBSZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSUTFZM1lqZ0tRVUZCUlVGM1FrbE5SVmxEU1ZGRVVYWXpVa2xRZGxFNVlUQnJObGxHWkZSNWFERllTMkZ0V1VndlJtZDZTMmhCTXk5S1ExUnZaVzgwWjBsb1FVbHhZUW95ZGtabU4zcEZWelZPT1dOemNtWmpkMGhZTlVOd01GTnFlRVoxY0dkSmRrZFdXWGRtYTBRMlRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVkwRk5SMUZEQ2sxRFNXcEVNbVl4UlZKaVYzbFBRamRFUlhOT2JXUnFUbU5NWkhKT1NuUjJhVk5wUm1Wb01tSkJNMWczSzFkR1FuSTBTblZWVkZocVZFSlBlbEF2UWprS2JFRkpkMGgyWTNGNlkwRnpjM2RzZDBzM1N6Qm1ha3RMUm1KUk1EZHFkMjFLV1haNVFqUk1iRlEwV25Oa2RFVkhXbHBUWld4U1FWY3JVbVpwUzNkMFdRcHNSSGwzQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1666486632,
          "logIndex": 5669854,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "90e7b30a96c22c390c339676d9880c85c1e88342",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3305298588",
      "sha": "90e7b30a96c22c390c339676d9880c85c1e88342"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

