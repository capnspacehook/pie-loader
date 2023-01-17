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
| `latest` | `sha256:62ab83bb5e930ff483c7f6a7de83797565943e3026e9a30d04a9dc25a5379298`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:62ab83bb5e930ff483c7f6a7de83797565943e3026e9a30d04a9dc25a5379298) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:62ab83bb5e930ff483c7f6a7de83797565943e3026e9a30d04a9dc25a5379298"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f6d3bbe8aecb87103d1e9ea0c557daaaf018a980",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQD1wzWcIQf94SFtOt7kh56CONCPYjodNDAMC37ZHaJXLQIhAPEUZOTEeLfQ4eRBzFgOtuaaLHEWeFLfGoDZsAJtMPvV",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlNWY1NDA0ZWJkZjhlZDY5MTk0OTI2NmI5YjIwNmNmYTIxMzIwZDYyYTdlYWJmMjcyZmY0ZjMwNTc3NDk5ZGU2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJSFpWV2tCTHBoRWJIQUFTQVdseVNMTUd5NFhZeEltRk1ERDJIVHJPK0RLbEFpQmx1N3ByZU1UM0U2S1UxMGJRWm0zZytqSWJTVTZZN0ttbThRWll6TjRSMXc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVllqQnVjVnBpU1Uxdk1YUlFOMkp4TVhSV1JVTnhUU3MxYUd0WmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlROTlJFRjZUMFJGTTFkb1kwNU5hazEzVFZSRk0wMUVRVEJQUkVVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZpZEhkYU1UaHpkV05oYzJ4aVJ6aFNaVVpVWm1WT1VtRkxSbFl6WkZVNU1URTNhMWtLVGpKSU5FbG1TbTUwT1hKcWFXUldZakU0VlN0UlYyOXFlazFKYUZWRVdYcDZZMEptUlVaVWRIRXhUbUZwVTJSNGRrdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZPSzBSSkNqSlpRVE5wTTBkMlEyd3lVamhHTW5CS1RESXpiRzV2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxT2JWRjZXVzFLYkU5SFJteFpNa2swVG5wRmQwMHlVWGhhVkd4c1dWUkNhazVVVlROYVIwWm9DbGxYV1hkTlZHaG9UMVJuZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYT1V0YVlsb0tRVUZCUlVGM1FrZE5SVkZEU1VoeGNraHFXbEpPT1RCcVRuVjBkRzVhYUdZclozbFBVakEyVld4R1RXdEtla1U1TTA5bVJIaHBhME5CYVVGUlUyUktXQW8wTVRoeVVrVlBOVnBWUmtka05rMVVTVlIyZERCNVdGWjVRVFF4T1c5bVEwOVJTMGhMVkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha1ZCQ214S1FXSklNazV0WlhsRk5FOU5kRUYwTUVsbE4xaDJhelY2Y2pObGJGQklkamhzYjJ0WFpVUnNNbEptZWxjd01EbFZiUzlPV0Zsck1FVm9Wa3QyUkdRS1FXcEJTREpSVUdnek9ETlNjbmt6VTBRd1IyWjVZVFUxY1dvMlJqaHdTMWRuWW05cWFIWlZVRVZ6TlU1UU0yUjBiWFZ0UzNsVVdGWTVRMDVEVmxGeVdBcHpaV005Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673915924,
          "logIndex": 11330521,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f6d3bbe8aecb87103d1e9ea0c557daaaf018a980",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3934989095",
      "sha": "f6d3bbe8aecb87103d1e9ea0c557daaaf018a980"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

