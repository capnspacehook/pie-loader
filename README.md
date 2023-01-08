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
| `latest` | `sha256:a527d1a2146c7ec21d9032591beff8bffd6c853e96fbc1653fc585040d185f77`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a527d1a2146c7ec21d9032591beff8bffd6c853e96fbc1653fc585040d185f77) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a527d1a2146c7ec21d9032591beff8bffd6c853e96fbc1653fc585040d185f77"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f496263432dfd68b0f406caae08e48507b2d2a7b",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDGgVA2qCyWfor2D4+XDJ9loT6dY2g2e35ggt7znf9LUAIgBM+5Vj5dQds+XX5UB/xITdcGJdFJiACISoQnFoEQ2WI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIyYmIyYTgyZDc2MTRhYjc1ZDhiNzgxOWU2NmZhYWE1NzUxZDRhMzQ0YjlmZmIyNTc4ZjhkZjdiZWQ5NmE4ZDA2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUMwQVovblBHajgwMFE4ek9XRkVCQTIwN2ZTUDNvSnBmSHh6OGp0dlpQTXFRSWdjYm1OWE9IbHQ0L2dkYTg5TXFobVRabU5tcCsvQTVjdkc1RllKVnMvMTJZPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlMzUkZhSGQzVkhGTU1tVlNlVFZMYjJ4cldFMUpVbFJ2U0RGQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVRSTlJFRXdUV3BGTUZkb1kwNU5hazEzVFZSQk5FMUVRVEZOYWtVd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYzVWs1cVkxZG1NRXRRVVhKWmFrZzVhMVZWZGxSRmNXeHZUMHg0YjNCNEswTnJlVllLZFRGWFdXNHJUVXRVZG1abFNIYzBiVEZKTmtwdFFpdDBNVzF3T0ZOVVMwMXlRbWcxV1U5eFVYUnBZV3c1ZW1welZIRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZRUXpSS0NrSllTVmcyUzBWRmJqQTVaVEl4ZFZNMWVUaERWRGxuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxT1JHc3lUV3BaZWs1RVRYbGFSMXByVG1wb2FVMUhXVEJOUkZwcVdWZEdiRTFFYUd4T1JHY3hDazFFWkdsTmJWRjVXVlJrYVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYVHpBdllYZ0tRVUZCUlVGM1FrbE5SVmxEU1ZGRFRTczVSV3hyY3k4M1NWaE9kSEZvVmtGNmVtNHdZblJETm5oNVNFdFNjbEZZV1hGblprVXlNVlpsUVVsb1FVeHhlZ3BwU0d0MVdUTmxkRFY2WldrdmJpOWlPVk5EZVRZd01Ia3phRE5yZFhWNk9FeDBha0UyWXpsQ1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlEyUkhaMGQxZVRoNVExbHJjVlpDU2tvdllsWjJhMnA2TkhCQk5uWmFPUzl0Y21wSU5WRk1UVUV2UW05blNuUnJXR0ZpUTFOV1ZXZzJNbmRNVTNVS1NrdG5RMDFFV1RsemNuVjFOV3RDY3pGMWRIVnllR1k1U0VSd2MyWlVSRUZGZEhCQk56SjJaSGh0ZW5oWk1EQlVla3B5TDBVelNrMTNZemxhUlZaQ1p3cHFRbEZzZW5jOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1673138558,
          "logIndex": 10700067,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f496263432dfd68b0f406caae08e48507b2d2a7b",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3864643444",
      "sha": "f496263432dfd68b0f406caae08e48507b2d2a7b"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

