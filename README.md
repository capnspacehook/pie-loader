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
| `latest` | `sha256:e83a02341ab780bc57ba9be099ef96ea376afcf1e9b4191bf7963266ca526fc5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:e83a02341ab780bc57ba9be099ef96ea376afcf1e9b4191bf7963266ca526fc5) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:e83a02341ab780bc57ba9be099ef96ea376afcf1e9b4191bf7963266ca526fc5"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "0b735856955fbec02ac4d03f3c48f47790365d17",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDtS/WjYQOi/1r21jl51jiOZWhgZSlc6yN+YCGJkkCxnAIgHuvl6Vnsv9Gx81kvkg+LvRaHSqfx7sr3WQ+alIlq9Ag=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmYjA5NWNhZGQ3NjBiZTM2YjkxYzVlNDFlYTc1OWNjNTAyZWRhNzNkNGFjYzc0MDFkYzRiMjk5MmRkMzQwZTc2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNsaHNDTCtVb2piak9JZUtIelRjM2hEWGY2WW1yRGpWOVFhcUxXME9sRk9BSWhBS3lNbFJMR1RTb0VJM3lvV1hiYWxLVVhBSzFtOHJoODUzaDZEZ3BuVWFDaiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlRuQk9OVWRDTW5WMmQxWmhPRnBLZW1OeFlUa3hXbE5IUzFkSmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVROTlJFRjZUbnBKZUZkb1kwNU5ha2w0VFdwQk0wMUVRVEJPZWtsNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYzS3paS1NEWTRVVFZMVkhWYWVYaExOelZ1VEZCakt6RkxlbEZ2YWtkdVptMDBVR29LVTBScVQzRjZUMWNyWkdac1pWUnlhRUZGTkZKTU5HMXJaVVJyY2swMmRrbDFjazU2UW5veVVEUkVZMkZ4ZDBwQlVHRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZKUjJoa0NrZ3JXbU0yZUhaNE9GUjVSMmRYWmtWblpETm9jMWwzZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkWmFtTjZUbFJuTVU1cWF6Rk9WMXBwV2xkTmQwMXRSbXBPUjFGM1RUSlplbGw2VVRSYWFsRXpDazU2YTNkTmVsa3hXa1JGTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVY1VFdk4wVUtRVUZCUlVGM1FraE5SVlZEU1VSV1VERklZa2hLZWt4VVNFMVRTVk5zYUdsNVRXVjVWVnB0U0dKb2FFOTRNemhOVERKS1FXNHJSakpCYVVWQk9WUTJOZ3BvVDNCbVNFdElSWFZSWlVFeVZrcERiVGRyTjJOTVZXZDFWRWxOWVU1cVNTdFZZbmRMTXpoM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGT1VqQTNWMWgzZWtwWlZERmFlWHA1YUhwVlZXdE9NbTlqWjNsUkwyOXZUWEoxVUhkdGRtOUxVVGxZZW1WWWNVazNiR0UxTVZkMGJFVTFjMkpSWlZnS1dFRkpkMkpvUzBNMFdYUXpOV0ZsZVc1dmFrNUVMMFVyZFVKaVJXUXZTV3RrTVU1T1JtWjRaVEJhVFVwTFNXd3ZlRTloTTNOb2RqSnRZVUpuTm1KVFFRcG5ielIxQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670373461,
          "logIndex": 8558649,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "0b735856955fbec02ac4d03f3c48f47790365d17",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3634734600",
      "sha": "0b735856955fbec02ac4d03f3c48f47790365d17"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

