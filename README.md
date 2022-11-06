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
| `latest` | `sha256:5b9de253c6779e8891a23a843707e048641f89eec7f8604633e32029fa3af1a4`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5b9de253c6779e8891a23a843707e048641f89eec7f8604633e32029fa3af1a4) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:5b9de253c6779e8891a23a843707e048641f89eec7f8604633e32029fa3af1a4"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "46b59489ae24fd91481331d0564b75486fb19326",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIEh7pNzRf8xJlwR1jsIYtdYruc/UFvFN62ybYM3ovPVoAiEAyOc/KWnqs1ofYGgJa41FY7z9iBUGcXXTlIkROPKR+4c=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1ODViNWIxYjBhZTUxY2Y2ZThjY2M3ZmQ0NzA2NWE1MjU3OGMyYjI1MDRkNjQ2ZmE2MDQyMTUwNTg4YjdlMTBjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQ3dDYjNJL3JvM25uT2pUNVI5MFFsdVZOZTNmZDlabzQ0dTdpM0VqendlR0FpRUF0VjJXdStWRnJGWUEzT2JQdXdrc0tGY3NMZ1V2YkN0MWhNY0NiNGIvMmh3PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlVrRmlWell6Y1ZOWlJEaEdOVXB6ZERsWUwwZFRNVEJEVEZoamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVRKTlJFRXdUbFJOZDFkb1kwNU5ha2w0VFZSQk1rMUVRVEZPVkUxM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYyY2poWFpFYzJhRFUxUnpCUmNHdzJXRlJuYVdKTldVMDBUSGhVYzFkVGVXWXphbFlLVUdsdmFHMVpNbFZLWmpWTGRrdEZXakZDVm1kVk1IRldlbkZuVDJjek5HaEZlVzkwT0dZMmFuRnZNVWRhTTNsTmVqWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ5VEM5WENrcEhXalJXWkhKNFNsWTBOMFUyVldsTVRpOTJTalJ2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCT2JVa3hUMVJSTkU5WFJteE5hbEp0V2tScmVFNUVaM2hOZWsxNFdrUkJNVTVxVW1sT2VsVXdDazlFV20xWmFrVTFUWHBKTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTUzFwc1Ewc0tRVUZCUlVGM1FrZE5SVkZEU1VkU2RFaGFZMHBYYTBRME1VMVRWV1ExTDJWMWNGVlVZM2RsVTFocU1YRm1XbGhSZG1JeVZsYzNNVmRCYVVGNmN6QnpPUXAyUVRsR1MxWnVka2RHUkV4WlNGTXdaMnczZERsSFRIQnpTMEZpTmpCeVZEUk9Ra0YwZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ20xaVQxRm1la2hOUjJ0YVIwaE1Xa1J5WWpKeFVWUktWSEEyTVZNNGFHVkdRMDEzY0c5MUswaEtRbU5tVG1zM2JqZHBka1E1TURscE1ERmxjWFpqU2tNS1FXcEZRWE0wZWtGa09HbDBXSGxvWkRCSVduVlNUVEZOYzJOWFYzRnFVVzVIWTNGcE1qRllNbXcwTjJSblVpOHJTbU5zV1d0ellqYzRXRmxJU1dwak5ncGhVMlZ2Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667695549,
          "logIndex": 6589163,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "46b59489ae24fd91481331d0564b75486fb19326",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3402306080",
      "sha": "46b59489ae24fd91481331d0564b75486fb19326"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

