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
| `latest` | `sha256:1aa446656e114c576623be01d839ac19bab73999792e8d6cf91b03919e62366b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1aa446656e114c576623be01d839ac19bab73999792e8d6cf91b03919e62366b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:1aa446656e114c576623be01d839ac19bab73999792e8d6cf91b03919e62366b"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7bde76859b5cc402fe356e81d329fc38c8f6ba9e",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFzt3tHUWj0RVEayjYWXX6gqm5Xx1ho7J6zENYJOY7EVAiEAiGIXbciREagkQ9OmP7i/cYjCBuWALQ4y2UmVbKZAHCA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhNzI0OTg3NmI5YmFkY2I3M2Y0M2M3MTJkOTg0MDk0MGIzMzRhNjQ3MDY4MTFmZjVlNzhhOThjMDMxOTdjMWU5In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQktwbWNxTENSU004WkdpRkVpalA5TUw0ck9mQkthcDZmM0JDWTUzbloyZUFpRUE3ekF1UDcvMXN4MEpBa2MwVy9ORDJEcElWUEpIL3RNL2w3Q1lNNjdZSzEwPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlZVZGlTV3N3UWl0aWNqRnpOeXREYkRONE1YcHNVVFZhVVU1RmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVhsTlJFRjZUMVJKZDFkb1kwNU5hazEzVFdwQmVVMUVRVEJQVkVsM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZWTkROVVRWWmtOMnMwUldSa2RtNHdOMWh5Tm14emJqbHNRVVZGTVM5SGJFMUxVRVVLYmk5QlpFTXdkVUpPYVhWalNGcEpZM0o1YzB0NlRtRXhhMnB6TlZRclFWQmhiMkpMYmxad1JXUm5SR1pQVURjeGMwdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZVY0dWbUNsWnFWbEp4WWtsWGFHeGhRWGR5VTNsWmNXVlBkRkpGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOWmJWSnNUbnBaTkU1VWJHbE9WMDVxVGtSQmVWcHRWWHBPVkZwc1QwUkdhMDE2U1RWYWJVMTZDazlIVFRSYWFscHBXVlJzYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaVUd0RmQzSUtRVUZCUlVGM1FraE5SVlZEU1VKUk9Hc3plbk00TlUwMlJrdGpaa2xVZFZSTmJubDRaSFJaV1ZBMWMwNU9OSFp5VEdORVN6Z3pVMGxCYVVWQmNFSjVTQXBGYTFVNWRuQndURmRtWVVsUVdVWlNTbXRQV1RGV1drZHVXblpuWVhWdUsxZDFLMEYwV1UxM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xwYU1qWjVlakJ4TlZWWVlsVktWMGs1WWtSNGRUQnFia0Z6Vm1oeGVHUTJOM1JIVGxKUU9HNXNhRXN2Y0dGSE9TdFRUVU5DU0hBNVpsSmhUR3BYVW1ZS1FXcEJhVEpFVEdKbGMzWmpWVGh0YmxoUGFrWTVRbEV4VTFOc2RHMVBRaTk0YVZCc1lXczNTMGREUmxNdk1UWkZlSFE0T0ZNdldXbGthbEF2T0VRMGNRcExUbTg5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675298384,
          "logIndex": 12442957,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7bde76859b5cc402fe356e81d329fc38c8f6ba9e",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4070087817",
      "sha": "7bde76859b5cc402fe356e81d329fc38c8f6ba9e"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

