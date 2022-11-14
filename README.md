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
| `latest` | `sha256:1b0efb525e09e7a8392b4adb7739f5953c2629f3ca47da2afc50dbce28df0ac8`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1b0efb525e09e7a8392b4adb7739f5953c2629f3ca47da2afc50dbce28df0ac8) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:1b0efb525e09e7a8392b4adb7739f5953c2629f3ca47da2afc50dbce28df0ac8"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "b7ca0a5314f25abab100685426fe41a62e7669ab",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIAObrPGeyE2NJOSYUk6XKLTCQ4lOVoE+e0BmkVj8LDp+AiBusHOhmPTpDxAprI3C/jWy0TYSnmlPcbpR429TleeT4w==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxN2Y4Y2NmMDZjMzUwYjkwYzM0ZDJhNzZmMWFiYWQ1MmM5NTNhZjI0OWNkYzc0MjFiZjQ0Njg3YzhiNzliZDA3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJSHJCaTMwUkxHT2dvRzlHTEhCMXprRGM1YkhSN1dESTBadkErZXY3b3VFQ0FpQkt3MWFJVlJGT3JFQkF1WDhUbGRzVFlKVGJaTkN3QzhvUGMwbitZZFFEYVE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVldWbENiazF6TDJFemJXSmxSRTlXV0hOTFFWaGtMMkZoTjA1dmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRCTlJFRXdUVlJGZDFkb1kwNU5ha2w0VFZSRk1FMUVRVEZOVkVWM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVY1YjNSdlNYZzNkalo2TTBaNU4zTkpjbVY1UTJaMlIzWlZWVFZqUVhac04yeEZRMjRLUzA4eWFFbHRVRFl2VlcxemVtVkJaRXgxUWxCNUwyNXNaVmcxU2pJclFteG1ORE5DZGxoRGEyZEpRM0YxVm05Sk5YRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV2UnpGSUNsVTRUbVkxZEdwV09EZHdSalZJVlVKb1MwbDFTRzVGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdsT01rNW9UVWRGTVUxNlJUQmFha2t4V1ZkS2FGbHFSWGROUkZrMFRsUlJlVTV0V214T1JFWm9DazVxU214T2Vsa3lUMWRHYVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTZW14VWNYb0tRVUZCUlVGM1FraE5SVlZEU1VkWWFYRm9RMkZ6TmpGTE5tOUJhVFZJVTNCMGIwTjVhSHB5V1dWa2JrcE5VbmhQZEN0NGEySk1aa1JCYVVWQk1GcEJUUXBvV0UxWlZtOVNaV2M1UTNaWVMzbFBZVWRJYjJwWmJVd3hWMXAwWm5Kc1YwdFdVMDV6VW1OM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ21aNVJWVllOVVJtY1hsblZHSnBka1ZsVTNGeFMwOXNaVkVyVGt0clR6QTFkU3RMYkZnNWQzTkRhM2R5V2xkNlUxUjBUSE5SY1hjMmFFVTJWa1ZOZG5BS1FXcENRMGRMWjNjd01GWk1VRGRZUkU1RlRYVnNhR0Z0VGswNVdXWjZjR1V6VkV4SlpVeEtSUzlvUlZseE1FVktjUzl4VUhSUVp5czNRVmhMV0RkT2J3cG5SMEU5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668386500,
          "logIndex": 7021183,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "b7ca0a5314f25abab100685426fe41a62e7669ab",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3457652801",
      "sha": "b7ca0a5314f25abab100685426fe41a62e7669ab"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

