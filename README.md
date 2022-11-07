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
| `latest` | `sha256:fdfbcaaf3e53ada24a20cbdaf4e097265f6a403cd479c3dc343ae4c9cd13a96a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fdfbcaaf3e53ada24a20cbdaf4e097265f6a403cd479c3dc343ae4c9cd13a96a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:fdfbcaaf3e53ada24a20cbdaf4e097265f6a403cd479c3dc343ae4c9cd13a96a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c543221ae4e1a70b8d8e1f36093eed4fab9224b2",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCYYeRNWINCWX6yIXQPij2Pf8mXcwUhL+49Qvq5OWE6GwIhAKpkH91HsJBHstoRzQYRdhdAszzgE91MQqKl404DUpJx",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlYjA4MTU1Y2MzMjJjYTkxYzc2YWUyM2M4NDI0YjE4YjM3ZmY4M2RjZDg2ZTM5MGU5MjE3Mzg4NTEzNjkxYzcwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQkUvMWZKbXh2MEpidUxUS2FkREg0ck5JS3NQQnFxT0tEZlppeWpUdVJ6UUFpRUF4MFRBYTlwS0JQWm80bzJPN3RPOWVHODVBMzJIaXNkU2tEWFA4L0xlK1NjPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlJXbHpja05RYW1KRE4wRnpWWFp2VDBaaGRrRk9XRFpxZGs5amQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVROTlJFRXdUWHBCZUZkb1kwNU5ha2w0VFZSQk0wMUVRVEZOZWtGNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ6ZW1zMlprWkVVWFkyZEdsMldHdFpWbVpuTjI5clJrUklNaXN3ZGpsRVVUQlZhSElLWkN0c01uTnhiVEo0VGpOTE1VeERSVk5QTVVka1QwUk1OMmxsZUc1T1dIVmhlV0V6VUdnM1Z6WjJTSEJKV2k5a1JYRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzWW5KMENrZzVaekJpYUZSdGJVTXlaM05CTTNoWk0ySnRhRk5SZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwT1ZGRjZUV3BKZUZsWFZUQmFWRVpvVG5wQ2FVOUhVVFJhVkVadFRYcFpkMDlVVG14YVYxRXdDbHB0Um1sUFZFbDVUa2RKZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTVUdsdFpXNEtRVUZCUlVGM1FraE5SVlZEU1VNMVJWazRTbmxoS3pnMVlVczROelV3UWpCNlVteHdZbUYxV2poQ2QzaE9ZMVJqTm5KQlVHa3pVR0ZCYVVWQmFXcFBkd3BvYm01alQxY3ljR1ZuZW14Q04waHlaMVJWV1U1VmNHaG9SbFV3VDFWNGJIRkxXREZuTUZsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xWcmNqSk9ZWGxUZFU1amVpdFpOa3AyUTFORlJVaFJWV1V5ZUN0U2NFRnlUQzlQUXk5WVVuWjNSbXhaUlVoMGJHVTFXV1ZXZGtJNVZUUlNSek5UU1ZBS1FXcENkR3B5ZEU1V1pXcEtXa3RGUzNabGQzTTBVemhJWVV4WFdIVlhlVFp4VjNGdVNtdE5TVXB3ZVdSRmJXWnRObFU0TW5CTFNqWkVibkZHYmtsM0t3cHNMMGs5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667781815,
          "logIndex": 6649091,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c543221ae4e1a70b8d8e1f36093eed4fab9224b2",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3406723963",
      "sha": "c543221ae4e1a70b8d8e1f36093eed4fab9224b2"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

