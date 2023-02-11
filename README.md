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
| `latest` | `sha256:5100fee91015e2dda15f2373896bd42c2eaf10c853dbd47c5d386a606a1e5ea3`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5100fee91015e2dda15f2373896bd42c2eaf10c853dbd47c5d386a606a1e5ea3) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:5100fee91015e2dda15f2373896bd42c2eaf10c853dbd47c5d386a606a1e5ea3"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4d51c8f83dcf3ab400146d5d15c238fc191abe14",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCICqeOxh+wd4qvlRQaej0noAP62R1GwfhadC+gcT/w9noAiBLCP5o9SSXMTQesNknsxdUuwvZJZwfzovpTZpJ8qxM5Q==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4Mzc1ZjlmODQ2NDAzZDRjOGNkYjYzMDQ4NTgwMWRmODMxMDk4NzE5NDBkZjhmMTVhMGIwMTU4MjkzNDZiOWY0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQVJPR3k3ZjFXWjZlTkVvMXJVOFhTdFJlU09CVGhwZmdYQ0J0SHFRZGVwWUFpQWZsZTBSbmZVQjlBUERTZjM5RkhlUDlYU1VYQmNadHhPUmJDditUVkpsTWc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlVIaDJaM3BwZFhKcVpHWllZbWRLYTFFdmNteEVSRTAyZUdOemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlhoTlJFRjZUWHBWTWxkb1kwNU5hazEzVFdwRmVFMUVRVEJOZWxVeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZNU0V4SE5WYzJOMlpGWm5CSk9IVkxjV1JuV1RsS2RXdDNRakV3TW5obk5DczBlV3dLWlZKb2EwNUhhbXgwYURCc2VERkxjV3hyZFRZdlZYUkVZM0U1WVVWdGQyODJiVEZQZGpKVWRVczFRbGxPT0doR2NEWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlU0SzNaV0NrUnFRbkJ5YW0wMFJUbGtNM1lyZG5kcWJGcFdkMk5yZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCYVJGVjRXWHBvYlU5RVRtdFpNbGw2V1ZkSk1FMUVRWGhPUkZwclRsZFJlRTVYVFhsTmVtaHRDbGw2UlRWTlYwWnBXbFJGTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaT1RWS1pIb0tRVUZCUlVGM1FraE5SVlZEU1VObVduTkthSEkzUzI5d2MzWXlVMGQyTlVsdE5VazJkRFpwTlZwT1dsaG9LM0p1UzJkMVZXdzNiMWxCYVVWQk4xWkllQXBVVkdGMVRVWjRNR3Q1YmxGclZrZEpkbGw0ZEVGQ1MyaDBNM0pQVERCVWQxWnZWRXRwWW05M1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xWbWEyUklZWFZzV2pkck9VTktTMWxsU0RsbWJFUlZNM0Z2TkV4bk56Y3dRM0JHZUdaaGRFeEJSR1JpYTBaNFNrMW1ZaXRtUzNJd0wwUTRiRUpCVDJVS1FXcEJiRFJhUTI4d1psZGhXRTV5Y3pSYVVGTk5SbmxTVTBSMVdIcHljbTFaZVdwRmVWaG1WbXcwVVU1QldVSkZjMnAzUzA5blVYVnVSalYzZUVoVlV3cEdVMnM5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676075662,
          "logIndex": 13080826,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "4d51c8f83dcf3ab400146d5d15c238fc191abe14",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4148809590",
      "sha": "4d51c8f83dcf3ab400146d5d15c238fc191abe14"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

