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
| `latest` | `sha256:7ab7d23b7b28bb238c044ca5ee30c0192510b2651ba94635407ec7bb40c9e039`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:7ab7d23b7b28bb238c044ca5ee30c0192510b2651ba94635407ec7bb40c9e039) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:7ab7d23b7b28bb238c044ca5ee30c0192510b2651ba94635407ec7bb40c9e039"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c7fcba8cfe5ecee8a4ff2f919de1ab8921a685a6",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCG0lJWyI8e5sFUzDc87Od5xg9AZOC2vhe2v4amwlVNlgIgcSWvgzRysoOpXcD63g8kYrt+GhyIUkPpnMpklfIjC6E=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIyY2JlYmI2ZmE5YjNkOTJmYmExZWNmNjkxOGFiOTFkZjZlZTE2Zjk5NWUwNjljY2M3MTA2MzkyMjNjZDljMTNiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURkaTNYVWdUUHhnQ3RyYXFjUXV4QkwzTkFtYVB0QzRSc0tOU3E3Yk4wWWh3SWdaV09PdTI0Zm9sdnBLc3RJSW5hTXdxd3JIajFWRiszOUdnVDB3V3diQjdFPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlJGTlRkVzE0U0ZOUmEyaE5lbmRPYjFsTk1VNXJNa2szY1hSamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVRKTlJFRjZUbXBGTUZkb1kwNU5hazEzVFdwQk1rMUVRVEJPYWtVd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZXYlRGclRVaERkMk5LYkhFNVJHVmFiM0ZLTm5OWE15dGxNbkJ6VVhsQmMweG5PVmNLUVhsYVdGSnFVRU00UXpkTGRYVXhObmxEU1N0bVZVdHNSMGt4T1U1SlpFMUtlR055UkhkaGRGSTFWRnBzWmpkVmNtRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZvT1dwRENuQnNkbEpXYTBGV1NHRjVLeXRHVVdzNGVGRXZaa1Z2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwT01scHFXVzFGTkZreVdteE9WMVpxV2xkVk5GbFVVbTFhYWtwdFQxUkZOVnBIVlhoWlYwazBDazlVU1hoWlZGazBUbGRGTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaYTBwMVdFOEtRVUZCUlVGM1FraE5SVlZEU1ZGRGMxaGxha1pJZVdzelYwSmFObHBHWW5KYWNGUjBlVFpUSzNONVpYaDZSVFEwU0hvclNWQmlNakpIWjBsblpGaGpaQXBMZDJWVk1EaE1keXRWYWtGTVUzVkpkV2NyVTBSeFQzbzNOREV5VVc5dFRYaFhhVU14TldkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2tNMk5tdEthVlZGTkRWM2EwRk5ieXRHZVhWVVMwZFdTV3huTWpKdWVVTTBjbTFQVDNGVFJHaHlOMUJFTkVwT1ZUQlFiMmx2YUU5SWR6UXllbUppV1VZS1FXcEZRV2xLYjNWSVpVRkRSU3RWUjIweWVsTTFSSGd2ZVVFeU1XWmljRTlNYWt4YVEwbFlhVFpQUTNKUWVXMVhRVGM0ZWs4eGN6Wm5URmx0WjJ0eE53cEJjbFZ5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675643793,
          "logIndex": 12704096,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c7fcba8cfe5ecee8a4ff2f919de1ab8921a685a6",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4099245365",
      "sha": "c7fcba8cfe5ecee8a4ff2f919de1ab8921a685a6"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

