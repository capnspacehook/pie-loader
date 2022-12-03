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
| `latest` | `sha256:cfd584a3b8dcf5bc61cd9dbe4b10ae78b81dbfac6b3d079a52181af76ee8d662`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:cfd584a3b8dcf5bc61cd9dbe4b10ae78b81dbfac6b3d079a52181af76ee8d662) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:cfd584a3b8dcf5bc61cd9dbe4b10ae78b81dbfac6b3d079a52181af76ee8d662"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7cbeb1817c8fc854bf51108078e193464a9a4465",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCjQIDVJDGmhXjUAM4qxuhuz0M5kCCl2fT+P9ILYxFM5wIgJmhrkoXwz4nu1lM/MZG9maYrOvFdmnT4bRm7HcD+RIU=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJkZjdiMzUzYWUxZTVhOGI4MDI5Nzk1NzBhMWZjMjdjZTM4YjhlMzYzMjQ0YzY0NmU1MTNmYzRiNDNhYzg3YmM0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNBWjRVMWd6akpiWVBnYXlpU3JsZyttRFp4UTB0VHhWclZsb2F0UjdYcCtnSWhBUGdMQ0l3RlJhZ1c4WEx6MmU4cGhna2xDZTF1STNjYjhzTit0VGdRTWp0eiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVldHRkphV3R5Y0hBcmNWZG5ORzB2VUV0NE5GRkhiRWRsVmpodmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVhwTlJFRjZUa1JSTlZkb1kwNU5ha2w0VFdwQmVrMUVRVEJPUkZFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZoY2s0dmVpdGxlRUk1U1hkS1lsWXdSREJsTURad2VGVkVNRmxEVVZGeE9EaHBOM0FLSzBsWFEwOUZZa3hrVVRGa1pUUTFNVk5wZUZCelNXcFZSa1IzZFRZd1NrMVlMM2hyYld0aGRrVlVORXhoVlZRMWVqWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZhVVhkckNqbFBNbGRqZWpSUFEwWjJkbHBhT1hBNWFDOVRSSGMwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOWk1rcHNXV3BGTkUxVVpHcFBSMXBxVDBSVk1GbHRXVEZOVkVWM1QwUkJNMDlIVlhoUFZFMHdDazVxVW1oUFYwVXdUa1JaTVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVVm1GRUsyd0tRVUZCUlVGM1FraE5SVlZEU1ZGRFVUUkVlRk5QUms0NWJreFJhMHRFYlROYU5VZEVUMWR2UVZWcVIyWlpTMU12WkhCbk1TdHFlbkkwVVVsbldYTTBZd3AyTkhWSVEzQnJiRTFhTW1KcVMyNTJialp1YjJwMFQxRlVkakUzTTNGbGRtRjBSREJoUVVsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGSldsbGxOalpuTUZNM05GRk1lV1ZEVDJkS2JVVlBTVVZNWlZGTFpqUnBNRXAwYVZsaFVGWjRiV0ppYjFoVWRtMVZTR0oyVlRKM056UkxjR2hMY0dJS2JHZEplRUZOVEZRclYwbHFZMEZsSzNRNFdqZGxXa2RMYXpRMk5FbEtNalk0THl0NVIzcHVXbWRRU2pCcVdrMUJTMnRWZUhwNlpUUjRXazEzWWtwQ0t3cFRPR0paTDJjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1670027711,
          "logIndex": 8327153,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7cbeb1817c8fc854bf51108078e193464a9a4465",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3606124328",
      "sha": "7cbeb1817c8fc854bf51108078e193464a9a4465"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

