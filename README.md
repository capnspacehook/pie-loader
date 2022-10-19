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
| `latest` | `sha256:58888ea2efe763e795d7df516ff6ba9be8c50f856ca1606daf39d6a1d8a63f8d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:58888ea2efe763e795d7df516ff6ba9be8c50f856ca1606daf39d6a1d8a63f8d) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:58888ea2efe763e795d7df516ff6ba9be8c50f856ca1606daf39d6a1d8a63f8d"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c91634e6064693b8e958893e1cec2b4fb57a5db4",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDQIKdByl1z5fx7+Olswj4E2CItc2z9o7MYw69BwarlNwIgcSF9HZQtNZpMYeSbON5wDwqW0Lx28BPI/pXY5yHBgis=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1YzQ1OGFhZTNmY2ZhZGVkZjM4NGU5MjIwOTBlMGFhYTg4ZGIwNTZiY2ZjYTcwN2I3Mzc1NWIyYTk4NzVlNTEzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUM5cGdoQmlXcTBCOVpnMndIM3J2bmZYNFNUcmNLUk41NFZ3Mi9YMXh3T3RnSWhBT0FzZ1ZFZ1hWaVBGMlVqUGR2UjlpVjhJSXhzS0dxS3VlMFhyWkRVNmV4aCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlluUndkMkY2Ym1sWGNUWkhORVExUzNGQk1UWXlZbmRNY1dkUmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRWTlJFRXhUMVJCZVZkb1kwNU5ha2w0VFVSRk5VMUVSWGRQVkVGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZFYmpodWMyZGhZbVo2Vm1wWlJ5OTBaRVpuTW1neVFTOXpXaXN5TjBaNVJuSmtUbUlLUTNkeGJVMTVZV3RQUmtwNU5XSkdPRVJPTjFCTlJYRjNiR1JpYm5aQllWcFFjMGhXVDFkaU5VNVRkbGhNYkdOV1MzRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyWkhSUENtNVRSVVJWVm1WNVRFcElkVzAwYzFoMmFEWjVlamd3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwUFZFVXlUWHBTYkU1cVFUSk9SRmsxVFRKSk5GcFVhekZQUkdjMVRUSlZlRmt5Vm1wTmJVa3dDbHB0U1RGT01rVXhXa2RKTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxRZEhkRU5qQUtRVUZCUlVGM1FrbE5SVmxEU1ZGRGR6QklRMjkxY0Zac1VVVnBRMEp3U1M5bVEzaEdSMGhCWlZNMGFTOXlhV1l6U0ZaQmVUZzNhMUZuVVVsb1FVMVBZZ3BGTUVFcmRHdERRVTlWSzBOSlNrUnpiRU5YVmt4MGMyVnZUamhNZEdONVEzTk9WMHRVTWpoblRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlEzVTNVV1pwVmk5cmVXMWxhSGQzUVc4MmFrWlJWak52TDJwaFJrTkNXalZMUVhGcmJUZEVORGh2TDNwTFRVMDVXRmQ2ZWpSTlYzQlpaRXA2VGtvS2FYQkZRMDFEVm5CbVF5OVBSWEk1ZW5KVGVITlFXSEYxUWpSRWFWTlJObkZEWW1jMU1XdEtNVkZuYUZnM1FTOUhNWEpOU0U1SE9IcE9hbk41YUVJeWR3bzJUR2N6WkZFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1666141163,
          "logIndex": 5398144,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c91634e6064693b8e958893e1cec2b4fb57a5db4",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3278025248",
      "sha": "c91634e6064693b8e958893e1cec2b4fb57a5db4"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

