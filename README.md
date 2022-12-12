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
| `latest` | `sha256:c4210cb81611035a007145aa1291eef214f457748bf5f7e77077c17b108e39a2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c4210cb81611035a007145aa1291eef214f457748bf5f7e77077c17b108e39a2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:c4210cb81611035a007145aa1291eef214f457748bf5f7e77077c17b108e39a2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7828976b69c49c43f80e60e858d0f7ea69d367cf",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCgdYnGo+uo8n6KHhTyF9rb+iiX0Co0Dd80kw22ZAgyAwIhAKgcOt8Nsd/oxw04PRjbUuP/oo5j8kPllAKJSC/m2Hrs",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjODEyYzg3YjMzOTQzNjE2ZDFmNDRmMDdmYjliYTQ1ZDkyZGRmZWQ1NmRmMDI1NWU3N2IxYmJjNDExMzhkZTRmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQXEvNk5mNTg5UUpIZEV6V3lQQnhwNXVQV0lKVzVydFNYcGZWVjVUbjd2eUFpRUF1M2hQLzY1MWJMY1NRdS9mallzTWtuSTNrNEVHa0FLd213NHk2T29rOWQwPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlRqVm9WSHBKYUZKVGNTOTRTbE5wYmtkSFduaEdhSGh6YlZwdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlhsTlJFRjZUMVJGZVZkb1kwNU5ha2w0VFdwRmVVMUVRVEJQVkVWNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZTVEZGU04wOTRRMjF2SzJKSlVGZERjM2M0ZDBFMk1XaG9XR0ZYZVdRMWVFb3hlallLWm10UmREZFpOa3BuWWtwVldWcGxObHBIZEdwWmNFVnlWRzRyYTBaV2EzUjRSV1V3T0hwS2NEazNORmxCTm05UlZVdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUzTDFGdENqQm1Ta1Z2YlhSbGJ6STVjVWRxWmsxSFNVWldNR1pKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOUFJFazBUMVJqTWxscVdUVlplbEUxV1hwUmVscHFaM2RhVkZsM1dsUm5NVTlIVVhkYWFtUnNDbGxVV1RWYVJFMHlUakpPYlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWUkhoWU5Vb0tRVUZCUlVGM1FraE5SVlZEU1ZGRGNXbG5USEphYWpaR1IwVndNWFpOTkVWNFFrSXlWMGw0YWtWRlVTOUVkRmRPWlhkcmVIUkxkV2ROUVVsblFYTm9aQXBhWkdacGRYaHNibEJ4Y21OSE5teEdhWGwwVG5rdk0xWlVZazVDY0dONmFHaHJVVFJOU1VWM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ21WVEswSnZWMkoyVjNwWWFGaE1aSHBCUm1ObGRHOWtXRGRrU0VVMmJVZHZPR3hYT0RacmJGVk9WMUI0Tm5oNlIwaElibWQxUW5WaU0wUXliRzVTY0c0S1FXcENLM0UxYkhSTWMyZHZOazlvVkRFMVUyWkJiMU42TTBJd1ZEUlNSMUF5ZG5SWVMwTXljamMzVkVzMGJWTjVRV0o2VGpoWGFIcEVRbWhtWVhBd1FRcENXbXM5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670805572,
          "logIndex": 8894720,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7828976b69c49c43f80e60e858d0f7ea69d367cf",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3671592944",
      "sha": "7828976b69c49c43f80e60e858d0f7ea69d367cf"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

