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
| `latest` | `sha256:55a93545b55a857b9b275412d4ca7579ec877576e9c23f01a8c9239233ed1411`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:55a93545b55a857b9b275412d4ca7579ec877576e9c23f01a8c9239233ed1411) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:55a93545b55a857b9b275412d4ca7579ec877576e9c23f01a8c9239233ed1411"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "048ba20dd4c43144f8328813f018a4c921f28736",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCRd7AXwPzXAg+SeVKh/mPZdSIaeymNiAJcljpM/ysdQwIgDXOdbihBhdzn2iCq0a4brFCCpC5aR/HNNxjgA2uo2PI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJkYTgzNDdiNjEyNzQwNGY3YmMyNzA1ZTY1ODMxNGIxYjMxOGE4NzRmOThkYTdiYmUzYzMxZmQ3MzRlZjczZjdmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRFhKYi95ZjBySHJVR3FleENMYmlOSkxlblpaQWZMV3NWc2g4Q1E2ZStIQ0FpQjhLb1lpaWJiN0crM3dxL1EvL3VmK2pReEk5anFaMlVxOGNzdXRMYlk5OWc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlpXaHBiM0JDVGk5UmFEbDRPV294UkZWTFUxRldWelkyV2tObmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1ROTlJFRjZUMVJOTkZkb1kwNU5hazEzVFZSSk0wMUVRVEJQVkUwMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZPVkhkcFJVTmFhRXhrT0RoRGQwNU5XbmxyZWxjM2JWRTBUR1ZrVUc1VUwwcExkMDBLTVRCd1N6VnZibTFEVkRSRmRXNWtlV3hCVGpNdldIUnJaSHBWVmpGM1JITmpjV1ZqTUd0dmQwdHVXRGsxZGtWdmRrdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV5WVdscUNtbFlhRXhUYWxabFFraDZhVWxDY1ZWRFVqaHRjbmh6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkT1JHaHBXVlJKZDFwSFVUQlplbEY2VFZSUk1GcHFaM3BOYW1jMFRWUk9iVTFFUlRSWlZGSnFDazlVU1hoYWFrazBUbnBOTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZZDNGdGVpOEtRVUZCUlVGM1FraE5SVlZEU1VFM09Xc3JOMk14WlRSMWNtcDFSMUpLT0ZGRWNEZDFMekZ4YUhGdVJYWkdNSFZZWVU1Q1NHRlBWbTFCYVVWQmRWaDFkUXBVVEdGdGR6ZFJZbk5JVTFBdlZXVjJRbU5PZW10TlZUUkZhRFUwVFRObGFraHpiRlkzZVdOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xsUVNqSXdLMVp3WldSMFFXZGxibk5wU2pKNlFrUkxTWE0xYm1zMk5IQm1TWFZJTUVKNE9DOU5XWGhzZVZORFpYWTJOVU4yUldaMWIzUTJUV1EwWlRFS1FXcEJNR1ZNVjI1NVNYQlVWRGw0UkRGeFdVSjFiVWxEUVhGT2JtbEdVbTFTSzI4ck5UWnNSSGhJYzJOdUsyTllWR05OTVRsck4zSTRWMjVsYkZCNVNncG5SM005Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674780005,
          "logIndex": 12022846,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "048ba20dd4c43144f8328813f018a4c921f28736",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4020442957",
      "sha": "048ba20dd4c43144f8328813f018a4c921f28736"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

