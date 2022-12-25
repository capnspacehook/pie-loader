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
| `latest` | `sha256:a84a09e4161eb4aed8aba633ad899361238a87e94f9f1546802fca3b15af1787`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a84a09e4161eb4aed8aba633ad899361238a87e94f9f1546802fca3b15af1787) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a84a09e4161eb4aed8aba633ad899361238a87e94f9f1546802fca3b15af1787"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "3f494406f8a2362cd9068e3d32d2b5a7d92976ca",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIG48pDJ6YdKudqjB/rcI3ExspJYyWbYhWv+M4mYk4XPlAiEA1ukT3VFLfCGoSWfaEpXC+rCXAe3PPKPqMa7ffSeA6o8=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4YzgyZDA5MDBhZjcwNDA0YjUwOTdmMDBjZTNkZjVhNzBmNjI4MzM4N2MzMjYxYTMxMGRlYTVjNWM0NTk2ODI3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURUeHVvbFlFTTJCZzNWTkplQmxvSTZ2Y3FrTWgxT09HTTk1NUhaNEVyTDdRSWhBTkl4K2pHSmVjd1lZNmZNRVNxaFFnditTanE4UkpMOWdaaTB3RGc0MVYzWSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlpTODJRVzFQUld0cWRFeFBiMjFuVGtjMGIxQmtXR0p2ZW5sTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1RGTlJFRjZUMFJKZVZkb1kwNU5ha2w0VFdwSk1VMUVRVEJQUkVsNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ1ZWxWVFF6TnViSFpPWm1WV1dsQjFNRWxoUTNSTk1uRm5VRm95TUhwdFlqTjZjbE1LUmxOTFVHbzBVbkZLY1hCTWNIaFRNek4xVlZKeUt6WmtNVEJqUzJoMUwzSlNOVnAyYTBKRmJXWjVVbU5uUWxSWlNEWlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzU25aSkNtWm1aalZaU1dGSlNFVjVURmR3VWtjeVNrVldhR3BqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwYWFsRTFUa1JSZDA1dFdUUlpWRWw2VG1wS2FscEVhM2RPYW1oc1RUSlJlazF0VVhsWmFsWm9DazR5VVRWTmFtc3pUbTFPYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXUjNReVlYVUtRVUZCUlVGM1FrbE5SVmxEU1ZGRVZWVmxXV015UWpkUU1ETmxjbFZIVWsxQ1ZIRmlSVUpTZEhCNWFFTlBSVGxEV1ZwRWREQnpZM0EwZDBsb1FVMHplZ28xTUhwamVGZHZWU3RtVDBacVRqUldXbGRCYjNGTVRrdFRNWFpXU2t4amRucFVSemt5YTFCSFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlEzTndOa3hqU1hJMFdETmhjMWQ1T1RCVFduRkxRV0VyVGpNNGJXSmpTbUkwVW5sc05FVlZWRll2YTNaUVpEWkRZWEE0WjNKWlEwaFRRVkI1ZGpFS2QxUk5RMDFFYkVoUGFWY3liVkZ3UjJKbGFIZ3lSa3RRTm5kNGVFUjFiVk54UXpSSVFVbFZiM1pKUlc5eVIzZFhNazFzVkhadlpWZDFlRk5NZVRaNWFRb3ZSbXBhTW5jOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1671928722,
          "logIndex": 9780974,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "3f494406f8a2362cd9068e3d32d2b5a7d92976ca",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3773587676",
      "sha": "3f494406f8a2362cd9068e3d32d2b5a7d92976ca"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

