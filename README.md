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
| `latest` | `sha256:a6f2271428a8c007934fef56830b4654249ffd19b69e18d41715e96e09112fda`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a6f2271428a8c007934fef56830b4654249ffd19b69e18d41715e96e09112fda) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a6f2271428a8c007934fef56830b4654249ffd19b69e18d41715e96e09112fda"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "b84d137072196206c5cf2cec3f7a11ed89cf05e4",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDCv1pxQzvP2VPcwzyJFml1bjB4fW29blPzUtbZBLmb3gIhAK+tIfkBHS6RhCY4i/EiwDAOuy+G+bPbxjnTY7w7rDD9",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1YTIzMDhlYzA2MGE4NDgyOTY0NDk5OGIxODIwNTM2YWQ2NmE4ZDI0NWU5OTVjYjFiODcyNGViZjAzOWUxMTI2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQ1grazFNL0QySzBFTFVWMmlTUzhmSEVFWkJXU3hkYlU2a0libHFhQjZnTUFpRUFtejh4UU96bUpDeVNJeG5yZlowZXVEaEhNdTdjc0U2SG5NVm9qKzJnNnNNPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlRHYzNWSFJ2ZG5aeGFVVTFka013YmpJM2JuZHhWWGxMVTJWcmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVRWTlJFRjZUMFJSZUZkb1kwNU5hazEzVFdwQk5VMUVRVEJQUkZGNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZpZVc1S01FRnZhMFJFVkVRd1EwcDZUbFJYWWxNNEsyWjFaa1p4VkZoeU9UZE5aRkFLVldkQll6WXJTamd4YlRSM0wwUlNOalF6YlVFNFJuQk5aV2RFYUU5blRXVklkbFJJYldGcFlubEZWWGx5Y0dWalowdFBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZCZFV0T0NtcFJRVEJ2VDFweWRETjBZMG9yT0doc1NXMHdlVXhyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdsUFJGSnJUVlJOTTAxRVkzbE5WR3N5VFdwQk1sbDZWbXBhYWtwcVdsZE5lbHBxWkdoTlZFWnNDbHBFWnpWWk1sbDNUbGRWTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaZW01RVpXOEtRVUZCUlVGM1FrbE5SVmxEU1ZGRE1uaDBaaXRxVFdkc1lYVk9ZMmRCY0hkVWVXRmhkSE41Y0d0dE9IZHpaekZ1VW14dU1tWkJjbG8wWjBsb1FVeHJaUXAzSzNBMmRqa3pkREZGUTB3eVkxaEZTVXhHVVhWVFptWjJMMDFWZEcxUFdUaFZZMkpWYkZOSlRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxQ1VuQnFSblJhTVRONFV6VlVWV1JOTHpGSlNWVjBVWG96YlZoUFZreE1RWEpPZUVsTk1GZE1aSHBNVkRCTWQyUjFjRXBHVGxObWVERXlUR04yYlVVS2RsRkplRUZRZDFwRVRtUlpNVGRCUW05VVZYZ3dNV3hIU2twYVJtMWllbklyU0RWVlFURkpNek0zZG0xaldEWnRPR1prT1dSd1NrUnVlVkppV1d0d1RncFRaMHhpU2xFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1675903153,
          "logIndex": 12934617,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "b84d137072196206c5cf2cec3f7a11ed89cf05e4",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4129750970",
      "sha": "b84d137072196206c5cf2cec3f7a11ed89cf05e4"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

