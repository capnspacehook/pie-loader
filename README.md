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
| `latest` | `sha256:256c8f76cd2aceb965772a426673d7426b61e8c40e989c8e6bc673de57c4c978`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:256c8f76cd2aceb965772a426673d7426b61e8c40e989c8e6bc673de57c4c978) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:256c8f76cd2aceb965772a426673d7426b61e8c40e989c8e6bc673de57c4c978"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c2838f4565796f86044ba5297e07b46dacd2e7a1",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQD/X++NXueLmZPSMb2DE2QZvUoClfgwrHMp5BJu5WF1fAIhAJ9Q3ZKET40Uo6vadkmjDt1HOrhe98wDGB7yQAcC9u2E",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxNjk3Yjg5ZWExMGY3YjY5MzA3NDE1NWUxZTc4NGFkOGIwMThmZGJiOWZkZDg4ODYyYTFkYWM1YTE5ZDA0YjZjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNlWnpoS3p3SHhqemNKenZxV3JrMVhUUmExME1Ja2FSeU5XcTdIMFdlUW93SWhBUDJmVTZRYjgzY2RTWmNDTUg5WlFQYmhFME1sVHlFK3J6M2QyVEtPSTdiSiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlpFNDNSMjl1YWs1MGNGWkNhVzFSVEZwNWRXOXhZMHhNZDFoTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRGTlJFRXdUV3BGTlZkb1kwNU5ha2w0VFZSRk1VMUVRVEZOYWtVMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVU0UkVOVE4yVndTRFF5UkZkTGVGRjFPVGRVU0VWNldtOU5hRzF3U1dsQ01VWXdka2dLU0dGSFVYaE9RbVF4VVZvdlJtdDVibmh3UjAxaU5YQXlPR052THpWUlNqQlFjRkZwTVVWVVRFRkZLMEZrYmtsRk1XRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZPYldabENrRnVNVnBNUVVoMlZISnJUWGhCYVVrdmJIUTVZM1pKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwTmFtZDZUMGRaTUU1VVdURk9lbXN5V21wbk1rMUVVVEJaYlVVeFRXcHJNMXBVUVROWmFsRXlDbHBIUm1wYVJFcHNUakpGZUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTTkhaTFdHUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRFpFcEJUMFI0Wm10aGRXUTNkVEJGVmxnM1VsVnNaVTV4TUVveFRHUklSVXhVTVhaSVZ6UjNTVzgwZDBsb1FVODBUQW96YzBOc1ZYTlBVbmhaVDNFMGQzaGxPU3RVUkZKQ1ZHNUhUMkY2ZDNsSFpHSTBTVWRrUmsxMFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxSWQydEpOMWN2UWtkaWFHRXdaRzVyV2t3eGFsSjNPWHBXYWxGMmRtNHphM3BRYW14UVRXaFlkMEUwTVdGMWRVc3lhM0JEZVhneVVIUndMM0k1YW1zS1FrRkplRUZMYldWV0wzTm9hVk5sWVZaQ1RFZGlWUzlRYm14NGN6VjZjV1l4TUhocVFrMVRaRmMyYzFkRmRFbGFNR3cyVlhKTmNVcE9NMVJ0VTJSNU53cHBlbEZSV1ZFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1668472960,
          "logIndex": 7092386,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c2838f4565796f86044ba5297e07b46dacd2e7a1",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3466414676",
      "sha": "c2838f4565796f86044ba5297e07b46dacd2e7a1"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

