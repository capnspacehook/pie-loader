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
| `latest` | `sha256:660685044d849a46508c034ab956ec633c4fd8536a301fd0540b43784a4e8688`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:660685044d849a46508c034ab956ec633c4fd8536a301fd0540b43784a4e8688) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:660685044d849a46508c034ab956ec633c4fd8536a301fd0540b43784a4e8688"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4c2a8a4ce26c078c6005ab50198076c215741a36",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDQ+oT6jmzrVI8b+xEpaTjmpBE3Y246bTdmeCzrPFc/tgIgWVzejxFKUe/vLzpXpbvEqax8BO777dFA7Hl1EwtDHKo=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4ZjBjMmE5ODdkY2NlZGZjNTNlNWRkMGM4MGMxMmZjMDBmZWFiMTEzNjA3OTViNDk1OThlYWFkM2UxZTBjZWZkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRzkrZWN6dWJRd1dZblFXdWplYS9QSnVSWGhuRGkxN2d5Q3dxZTdEZjIwekFpRUFqVDl6YWRZa3licitCaE4xUmJXd0xYLzB0TDFOZFNrNGJzYTN4Y3ZkN1BzPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlZXeHhMelpwT0hCbEswNXFRa2QyTjJKV00zQjZZWE5KVm5JMGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxU1hwTlJFRjZUMFJCZVZkb1kwNU5hazEzVFdwSmVrMUVRVEJQUkVGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUxTW1Kdk0wNVVNVkpKWjJaUmRrTjFVM1JQYm0wNU9ISTRaVzlWTVVjMlRYaEtZblVLVEZndlZHVjRZVmRzYm1Gd2RWTlFjbE5TZFZaaFdVY3JiVmx4V0RkUGFHTk1OM0JVU2tsSFUybFZMM04wWm10VFlrdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMVlZGc0NrVnNaRkpCTWxnME0xUjFVRXhXWkVRNVNERmlNRWh2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCWmVrcG9UMGRGTUZreVZYbE9iVTEzVG5wb2FrNXFRWGRPVjBacFRsUkJlRTlVWjNkT2VscHFDazFxUlRGT2VsRjRXVlJOTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhTjNSTFprc0tRVUZCUlVGM1FraE5SVlZEU1ZGRE5TOUdiMUI2ZFc1dU0yc3lkM0ZDYTBOd1JVZG9PREJFUTB0bGN6VXhNVGRDY1hKV05WVldkazEwVVVsblUxWnFVZ3BpVURORmRXTXpVRVozVlRGVFZXWkJWVU5OYXpFclQzVnVOMkV5YnpNd1RsTldRbXBhZUVGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGTWFrTk5XVEEyWTBkb1VETlBiSHBSVVVoM0wwUkdieTlHY2xoUVpXVlVibTl4ZDI5WUwyaHBhWEZWWjJSVE9EbDNRMU5uZDFOa2JEVjRSMjVJUW1rS1NWRkplRUZOYkcxdVkwbFRVRmM0YlRoYVoyNDVZVzlGYkhOclptRlVaWGwwT0RNMmVYTjBNREl2SzFCVE5GcHFlRWcxVEdkR1JUTkxTbUp1ZFZaRFRRcG5SMDFSYjJjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1677112708,
          "logIndex": 13962889,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "4c2a8a4ce26c078c6005ab50198076c215741a36",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4248289697",
      "sha": "4c2a8a4ce26c078c6005ab50198076c215741a36"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

