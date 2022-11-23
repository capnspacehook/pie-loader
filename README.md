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
| `latest` | `sha256:1c663a1f1c215e591fdd30d54b51b693870ce4b16441442ee40322a5c907b6a1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1c663a1f1c215e591fdd30d54b51b693870ce4b16441442ee40322a5c907b6a1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:1c663a1f1c215e591fdd30d54b51b693870ce4b16441442ee40322a5c907b6a1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c4ab20df39bc96ad94a0bb35cd0da39f405973f6",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIAPb21ZQkrOsnUq1lP30xT2fc+YroOPg6HPgT6x6gLCYAiEAylj8W8fLrSmsdOwwTWg3aTo0W4lLnw9dVjvY5zvMgz8=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzNGVjYjcyZTc3YWNjNWU3MjMyMDFkY2EzZDJkMjA1OTk5YzRmNDAyNWU4OGQ5ZjA3ZDY5NWNjNzBiOWFhM2ExIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRTdtUDJyRU5LTGIzb3lLRFRuRWJjUnAzYlJRWHhDU1Axem5WdUwwMUs2L0FpRUFwcUZCTDRhQkZXRFZvQVY1UnpKc0kvbzdmcEk2V2ZIc1ErUlhOZGNZTk5JPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlZIQndRbkJaWlVWTFlWbzFVMGxMSzBnMVJVZExNVWROVkZOdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1hwTlJFRjZUbnBKZUZkb1kwNU5ha2w0VFZSSmVrMUVRVEJPZWtsNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZZYW01UmNFcGlSRWRHZVZCeGVUVnJjVmRHVVc4MVQwWlplRzVaWWtZNFNYRnhZMVVLT0VwT016QjViSGRtVGpkbmF5dEJhWGxWY0VwMk4xVnpiSFIyTTBnNFl5OXVkVFY2T1U5RFdVRllTblpETWxKeE1qWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZIWTFac0NtZEVVUzlsU1d0MFlsWnJPWEJET0hOa2NtOXBWRzFOZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwT1IwWnBUV3BDYTFwcVRUVlpiVTAxVG0xR2EwOVVVbWhOUjBwcFRYcFdhbHBFUW10WlZFMDFDbHBxVVhkT1ZHc3pUVEpaTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUYURaMlpFRUtRVUZCUlVGM1FraE5SVlZEU1ZGREsyZFZjMnRpZUdjd1dHcEtaVVp1VTFaVldXeElPVTlrVkVaaFZtOWhTWEJrT0VaRVpUUkxWVk13UVVsblFWUXlSZ3B6YW5aMFpIUklhbTE2WXpkalFWWkpXR2M1WkVaQ1RGUjBUV1F3ZHpFek4xaFFibGhvY1RoM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGT1V6VlllbXBPU2tKd01qRTJZbkpsYmtkc1MxQjJiMWgyYVU0NVVrRnJlVGhKVWxwWmRGVmtPVTk0TldVeFJHaENaRXRHTDJwMk4zUldaVkZUZVZVS1VGRkplRUZQVldnM05HbzVTVVJEYkU4cmJYbEpLMnh2VEZodGRHRlpNRFZxTkdkeFVEazRZbVZVUWxWc1ptSlRRM2h1UlRac1RtNWFTRzl0VVdGRU9RcHFValJQVW5jOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1669163875,
          "logIndex": 7653190,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c4ab20df39bc96ad94a0bb35cd0da39f405973f6",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3528243668",
      "sha": "c4ab20df39bc96ad94a0bb35cd0da39f405973f6"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

