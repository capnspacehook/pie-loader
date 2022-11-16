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
| `latest` | `sha256:5f3c241227cecd01667162d42636c11317ea308b7d8b79135f5aab3c60657157`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5f3c241227cecd01667162d42636c11317ea308b7d8b79135f5aab3c60657157) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:5f3c241227cecd01667162d42636c11317ea308b7d8b79135f5aab3c60657157"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "ee1949776297b260d8a3a74731d41ad94fec3a37",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCSct0OJV0IyiX0j8/8lTbNdxijQqMgId0X95ei+e8e7wIgPVT32fr//GbRKT0eQW7TX7IP94eA1m6Q2vB22ykmAvA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlNTBiNTFkMGQyODZkY2MzZTE0MzAzMzM0MTBhYzFkNjNiYzJlYWViMmY5Mjk2NGQ0MjU5MDcxNGExMGM1MmMxIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQmpEaFVtclZzaElnelFtV1pINmpGc1V4UEIwc1psS2E0dXFJY3NHb3lsZkFpRUE4R0RXYmtBZnZWYVBJY3BDZmVZZytGdS9XWmpzWG11VXJydkI3RmZ5L2FRPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlZFNHZjWFZ6YjBRNVYxRXJNWGR2ZVc5SVRYZHZja05zTDNwdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRKTlJFRXdUWHBCTlZkb1kwNU5ha2w0VFZSRk1rMUVRVEZOZWtFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVY0UlZKclpGQkhibmQ1UldVNE0zQTVabFpQUTNOdVVucHNaVWgwS3k5RGNGZDJjek1LVlRSUVNEaG5WWFZYYUVoSU5HZG5OVkJKY2s0eFdWWnRTVVEzYTNOaWJVZFdOVkEzWTNsMFZUWlRSRXRQTTB0TmRFdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlVyWVdaYUNsWmtVblJXTVRFd1QzUkxWRlZRVlhwNFNrZ3pZM0Z2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd4YVZFVTFUa1JyTTA1NldYbFBWR1JwVFdwWmQxcEVhR2hOTWtVelRrUmplazFYVVRCTlYwWnJDazlVVW0xYVYwMTZXVlJOTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTT1RRNFIyWUtRVUZCUlVGM1FrZE5SVkZEU1VkUVJUZHdSekF4WjBsbGVsaHJVR3ByTnpOc00xbEJlVnBLWkdGWlpWazBTbkJ3U2pacmEyWm5NbGRCYVVGemRFSkVUUXB1Y2xBMGNuSkJPRFpUUkhkMFIyUXdhelVyUlRWRlFtdzVVMlJIUm5ObVowUjZVVXRVZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0owQ2k5RFNUYzFabUV3U2pKU05sWm5hVmh2U1dwMmJtSnNjVGhJU1V0a1VuWTFSMVJ1ZFdFd2FYTm9kVFJrYURWaGFpOUlPRko1Yms1aVptOXlSMHBKVVVNS1RVSnFXVTAwZFRKUmFITjRXbXBrVVVKUWVVeDBkVFo2YjNwV2VFcE5jVGRRUjFkblNuSnJNV0p2YXpZMGJteG9jVzk0TmpBM1lsZHBSbnBuVDFWaWNRcFhkejA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668559414,
          "logIndex": 7167552,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "ee1949776297b260d8a3a74731d41ad94fec3a37",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3475374596",
      "sha": "ee1949776297b260d8a3a74731d41ad94fec3a37"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

