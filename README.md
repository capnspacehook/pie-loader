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
| `latest` | `sha256:4823131b7de989f4c3b8f845e529ef7e294a31d37885cf40d234fa9ca4e28384`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4823131b7de989f4c3b8f845e529ef7e294a31d37885cf40d234fa9ca4e28384) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:4823131b7de989f4c3b8f845e529ef7e294a31d37885cf40d234fa9ca4e28384"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "99b5099003cb519831b6f27f427511e2f0933c99",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIAdLvoB2SwMlrTFcYtIceJCZAAyqMo2HM2KByXt9NZ/7AiAHv1bgx7fFz+w0ruPRzEWvnydw2T4J9lh0fffniuU89g==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI0NzU4ZGI5ZDY1MjYyMTAwZjBmODAzMzIwNjJkZjY3MmMyZjg2MzJlYjlkOTJhMjBiNzBjNTYzN2QyMDIxNjZiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURva3NYUGs0LzltWmJKRW9zWWxVNURMS3VIbXdSL2k5eVZLdkpaTnkwbEd3SWhBTWpoWlV4ZEhaZjBENzA2d1YxZURoRDlPNXFaaFZCeldic0NUc2tPWkhKRCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlNEVlJjMXBFZGtFck4xRldOMnhrVTJOV00yWnpUMnhyV2tSTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFVFhoTlJFRXhUa1JWTTFkb1kwNU5ha2w0VFVSTmVFMUVSWGRPUkZVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZzYzJkbk9XMTFPV3RwWTNGcU1VaHpNMXBWU0ZoQ2MxVXpka2xoTDJSeVNFdHlaRmtLVjFkdmRYcGlaMjlIUlRWWFMzSjROMWMzWkVoWGRETTNUMnByTW5sMGNrTTRObE5SZGxSak1XOXlTR2R0UTBGYU1qWlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZOT1VvMUNpdGFVVXR0VVZFelFrWmxhWGswVW1aVk5YY3dZVVJCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWUFYwa3hUVVJyTlUxRVFYcFpNa2t4VFZSck5FMTZSbWxPYlZsNVRqSlpNRTFxWXpGTlZFWnNDazF0V1hkUFZFMTZXWHByTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSY21sTk9UUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRFVHSnlkVWRYWVcxRWFWTTNiSFZyTmtkeGJIRmpVSGhHVTJ3ME0wOUJiamMyVkdzNU1tNU5TV2xqZDBsb1FVMXdSUXBIV21ac2EzTjVWWHAyUWt4ak9GUkpaMlIyYW5KMVEyaERWbVV4TTFWelVWUTNZVUpEYVZkS1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxSGN6aHJjMVE1T1RaSVFsRmhRbEZqTVZkc00yd3hPVUpOVTBsd1JuTlpVR2hpWnpFMVZFNVJjVTVRUW05UWEzUnRObUZQYzNWelNEQTJZVUUyTkhVS1JWRkplRUZPV21WYVFUTlVabVZSVlhOS1pETm9lVk56ZDNseFZUQklNRmR5Y0VnMVJERklOak5sZUdGeVdIaHpjemR4T1dncmNHRXdlR1ZaUzFoeU1Bb3ZSVE5SYUhjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1667177737,
          "logIndex": 6189999,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "99b5099003cb519831b6f27f427511e2f0933c99",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3357784213",
      "sha": "99b5099003cb519831b6f27f427511e2f0933c99"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

