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
| `latest` | `sha256:ccd5a3d7422816c5328415967d26929476c76292a12adf15985197c0576fa3f5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ccd5a3d7422816c5328415967d26929476c76292a12adf15985197c0576fa3f5) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:ccd5a3d7422816c5328415967d26929476c76292a12adf15985197c0576fa3f5"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "348e74bd2e2e2e54ac8234d76853f4a38ce0bab2",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIEpYytf3ahpteMLfL+ox/AmPPJLS4YReML0m8U1uBqn1AiAPYp0eA9bpYaa73nYYI4oGFYBo8/noc2Fo0hBw9e/50A==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmZGE5NjcwNGY5ZGJjMDVmNjQyZDcwMmVjMzMwZDgxM2IzOWZjOWFiMTNiNDkyMGIyMGRiMGQwODg2NzFiZjhmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURCckdza1ZXc0VlZzF4U2UzN2ZtY3ZHczZGZWRiRTNnRUhRQVdEYjg2MVRRSWdVd2t0SFY3VWtvTzF3d2RsU3N4eUJtbG1vdHlrbGhFVU52T3JrWFlSSGVZPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlIzWmpZbGR1WlVRNFdYVk1VV3d5TlVFeGRGcE1kbWRZVWpsemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1hkTlJFRjZUbnBCZWxkb1kwNU5ha2w0VFdwSmQwMUVRVEJPZWtGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ4U0VsTmFFRjNVMU5oSzFrMWNtbHJXV2Q2TDNVeGVFZFViRU13T0M5WE1HczBVeXNLWmpKd2JXSmFNVGcwU1hkYVZtTllZVGxRVDBOUE1URjRhakp2YTJVMlVrOUJOelJQWkhGdlpXcEhjbXRpZDNoWFNIRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY2YWtocENrOVFSRWhuT0dSc1V6SXlhbWhqWjJSNWNsTkdPVUZGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwT1JHaHNUbnBTYVZwRVNteE5iVlY1V2xSVk1GbFhUVFJOYWswd1drUmpNazlFVlhwYWFsSm9DazE2YUdwYVZFSnBXVmRKZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWY3psdFUwSUtRVUZCUlVGM1FraE5SVlZEU1ZGRVdGUjVkbGhhZEZWblNtWlNORXcxTjJ0Vk5UUkthRUo1VFdWSGVXbERWalUyY2xGbU1rMXVZVGxMZDBsbll6RkpWZ3AzUWtGcVJHNWFhRVJDVDBwaVJGWTBiR2t2ZFV4SVV6QmFjMWx6YVZRMFlucE5Ra0pFWXpCM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGUVRrRm5SV1ZzWW1sbFZsZGxSM1ptYUdGUFduQlpaRzFJYUVrek1uRkZaV2R0TTBZNVJ6WnlUR0pIVFdGQ2NqSTVlRWh2VTNRMWRYUm5abU5tTUUwS1dFRkplRUZLWlZsM2VYUlNiRTgxYTJveldHbHNSMGwyY0dKNmRFeElUMnRRWkNzeFowbGtWMEZoZUZscFNteFZVMVI1V0ZGSlRUQnhhRkZKYTBGemRBb3lNRWRTV1VFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1671496649,
          "logIndex": 9445285,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "348e74bd2e2e2e54ac8234d76853f4a38ce0bab2",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3736380542",
      "sha": "348e74bd2e2e2e54ac8234d76853f4a38ce0bab2"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

