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
| `latest` | `sha256:398641496d42c876d711a780f418f585519f2045f913fbe2b6db89455f3a6d91`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:398641496d42c876d711a780f418f585519f2045f913fbe2b6db89455f3a6d91) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:398641496d42c876d711a780f418f585519f2045f913fbe2b6db89455f3a6d91"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "436427c45887b9919c56613f8548a6157672bf03",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIByW26yVzXmIRCuGQrdWoz7GNp6WquhzCd2ahPb+fHcHAiALjhscEEuXRKleAWIEc2HlZ4Bs49iB2NaruoKe9vXLqw==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4OGU5NTQzNDY4OWY0NDFhOWQ4NDhiZTQ5NTg3YWY3YjRlMDgyYWU1YjM4NjAxNjhkODdjNjVkYjExZGJkMmUzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRXJpcUxqeGNtV2pNajFJR2N2RitoTTIya0gzRjVWaGpMd2JUc1c1b0JaOEFpQU1OREhFWms0RXltTG8vVWt3cmYxY3BmbldjRm5FT1EwRzk0VHZ6NFZqL2c9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlJrMU5TVm9yTWpkSk5rbG9aamROVjBWRU9UWkpSMlJGUkRSTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxVFhkTlJFRjZUbXBSTVZkb1kwNU5ha2w0VFdwTmQwMUVRVEJPYWxFeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ1WVdSdlIyeFlWM0ZoZUVjemIwNTVRVk4zV2twd1pGVXJTbWQyTTJKdlRtcFViak1LU2pkcGNVcHhNMWR0ZEhCWVZWaGxMMUZHZEN0NGJFeDZVelozYjFOSGNITldMMFl3Y3pFeWFtTkpkSGRCWXpWWlFVdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYxZW5oNUNuUk5SRFJuUTJFcllVWkJRekJKYVZCTmJtc3hhVGhyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCTmVsa3dUV3BrYWs1RVZUUlBSR1JwVDFScmVFOVhUVEZPYWxsNFRUSlpORTVVVVRSWlZGbDRDazVVWXpKT2VrcHBXbXBCZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXWjJSaWJFOEtRVUZCUlVGM1FraE5SVlZEU1ZGRFVpOHdRMjgxYjBSVWVrUkxZMjVsWTA5MVprRTFhSEY1VkdObE1ISTNUVFpCZWpWSlJXVkhkMFZJWjBsblZVdFVSQW80WTNWQksxQkphVVJSVURsSWRHSm5NM3BYTlRBeFkxSk1OR3B6WVZkcVpGcDRPU3RUV21OM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGUU5XTk9PRmd4T1RsdVltSkxObFJWZVd0eFZtVmhia3BsYlZwSmNWRXZhMVEyTW05QmNXVlJkWFJSZEVVd1owaEdTMWhqTkZkWVowUllSVnA0V1dFS1YzZEpkMFIxY1dSRGNITnNZMlF4TUVGNFExZGlSakZsUWpGNlZHRkhLMFY1VmtveVRqUlVTVTFvY1cxb2FqUkxkMjFEYTNOVlpYVTVTRUZPZFZac2FBcG1kaTlsQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1672360630,
          "logIndex": 10106425,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "436427c45887b9919c56613f8548a6157672bf03",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3803951648",
      "sha": "436427c45887b9919c56613f8548a6157672bf03"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

