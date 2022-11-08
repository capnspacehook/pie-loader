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
| `latest` | `sha256:1b5b2bfa795952f4a8e9969d3f7bb2b70555bf8b46dd36fe3a599694feff7aa1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1b5b2bfa795952f4a8e9969d3f7bb2b70555bf8b46dd36fe3a599694feff7aa1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:1b5b2bfa795952f4a8e9969d3f7bb2b70555bf8b46dd36fe3a599694feff7aa1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "5ef0f80a73161e54d2b8b9127b00a6e2a86deefb",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIGHz4Jsakyu+uWpDq8/Ks6pE0ZYY8+/HdpRu20wK9YqGAiATVwWQtz5MgBKTiFwsnH0vtFC4S4lLdxCOrlWpwuUB+g==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhYWRlNjE1ZDYyMDhhMDJjNzhiNjg3YjE4YThlMGIyMTM5YjQzNTYxODExMDE5YjFjMTkxNzc5YmYwZDI1M2M0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURjTzkrL2lsMlZ0cTVOTkhuRWlXbEVIR2J5SzBwQmN1YjFPTTRQdlpBQ01RSWhBUEYwME5Wak5PQkt5dWJzdFRHbUxPbnlsZ1U1aGZOanBvVExhd0xoRmpXYyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlNHOWljM2t3UkZOalFXRXJOV2xDSzNwS2MwbzJabE5WU3pKemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVRSTlJFRXdUWHBOTTFkb1kwNU5ha2w0VFZSQk5FMUVRVEZOZWswelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUT0RWaVQyYzVVRmRoYlRkQlRYQndhRWxPV25ZdmNXbHBUVGRYU1N0TFpWWnpRbG9LZERFMFpESlJXWE5IVFRONWNIaHBOVVpxYkRaWGVYVjZkM294TldSYU4yOVRVelZLY0RaaWFVeFBNbTQxU0ZaMmIwdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZQUkVWMENqTnNTVzFhZUROVldFTlhUSE51VjIxVU1GRnBlbE5WZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGYVYxbDNXbXBuZDFsVVkzcE5WRmw0V2xSVk1GcEVTbWxQUjBrMVRWUkpNMWxxUVhkWlZGcHNDazF0UlRST2JWSnNXbGRhYVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTVlhOV1N6SUtRVUZCUlVGM1FraE5SVlZEU1ZGRVlrdGtiRU5ITW5CV2J6aHFZWEY2YlhKUFVtZzNhWGt2WW14VmFXMVJNRFZKZFRJMlZVdDZjWEppVVVsblVUSnFUZ3AyZGtkRGNXZDVVRVZJVkdsTllYcHZjMFoyU0ZOT05qTm5PVXMwTVhOak56bEVlazFZWlVGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ21GaVJESlNhbkZ6Um1zNWN6UXhhMk13SzAweWMyWkZVVkpwWjJaNFdYZEZTMDU2U0VreU5IaHdSMGxFT1ZkQmIxWkdVVXhwV1VVeWVIVTFaM3BQUmxnS1FXcEZRWGxhY200MFJHNDBRa0pOV1ZjeE1FbExhbGx5YUZwNFdsRTBPRUV3YlRaUmRrMWxjVXRMZUcwMlptcElXbmRZVlV0eFkzWjJaRVYyT0hKVWRBcHlVbXRXQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667868239,
          "logIndex": 6703108,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "5ef0f80a73161e54d2b8b9127b00a6e2a86deefb",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3415347932",
      "sha": "5ef0f80a73161e54d2b8b9127b00a6e2a86deefb"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

