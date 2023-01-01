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
| `latest` | `sha256:adcf88bfd5a8598d37e0bd7f4230bef029fae6b9923749714004fded2b4178e2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:adcf88bfd5a8598d37e0bd7f4230bef029fae6b9923749714004fded2b4178e2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:adcf88bfd5a8598d37e0bd7f4230bef029fae6b9923749714004fded2b4178e2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "23f175a72c2a27d874894d458b68ec7af51c38e8",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIAqYd6afa/c0APL/kUiCCqP/5CI5of0KjOFzFlx35zAUAiEAzkz+8qfIdmP5GthIrDdEJdORwKvmPuNTMkhy2NITBAo=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4YmEyYmMyZDhlZjU2YWMyMDFlMWI0OWUzYTRjY2IzNDYwMzI0YTc1MGMzNTJjZWQ0YzJjZjI4ZGFhMzdiMzI0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJR29iQzVIYWNjdEdheEE1T2tPOGZBLytTSHNBT0xNNnBwVGJ4NEZIaEQxekFpRUF5a1YrQjgvYnF0UnFHL20xZnh3d3hFOHQyNkIxejJTNjVpYi9PMVRsOFBNPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlNFMDRiSGx5U2xZeFVVa3piRms0U0N0Wk4ybDBhbk5WU0c5QmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVhoTlJFRXdUVVJSZWxkb1kwNU5hazEzVFZSQmVFMUVRVEZOUkZGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVU1Tm1GaVRscDFZVGxIVm1JMmNIWnRUVFI1ZDNablpFUjZUbVIzZUN0UmR5dEtZbllLZDNobVNFRkJaVWR4TUdsRldqQjBRbEYwTmt0SlpWbDFjbWxuUkc5VmMzQkdkQzlCY2xaSWVHVnZOVlpNV0hjeWNqWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ4UkhoWkNtd3dVMmxOYjI1WU5GcEJUbkIwYzNocmNDOWlOV2R2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsTk1sbDRUbnBXYUU1NlNtcE5iVVY1VGpKUk5FNTZVVFJQVkZKclRrUlZORmxxV1RSYVYwMHpDbGxYV1RGTlYwMTZUMGRWTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXY1hob1FVc0tRVUZCUlVGM1FrZE5SVkZEU1VnNVV5dHNlalZ5YzFkc2VEbE9abEVyYlROdVQzQnZOblJ1ZVV0Q1MwRnFURWhpUVd4ek9YVXdNRTVCYVVGb1dFaGFaUXBHYVVOcFdUWnpOMk5sUjBsalFURTRUbWRoUkVOeVQzYzFOekoyWjFWaU4ySmljRE5KYWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha0U0Q2tsUmVUaHBjRGhtUW10b1FVNHhWbWN5TldSaE16RjRZV3RCT1ZsUFNUUTNSMVp4TjFGcVEwSmxSMmhMYTA1T2MyWXhlR2xTYWt4eFl6YzRZV0ZDZDBNS1RWRkRWekJRUVhsbGNrWmFSbXRPTTNGSVNuQkNlVWR1YjFNeU9XSXZlVFJyWkRseFIwMWphRE5GYURKeE5rVXdSemRMWkVwdFRYVnZSMlp1U3pSSFRRcDNNRWs5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1672533664,
          "logIndex": 10227856,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "23f175a72c2a27d874894d458b68ec7af51c38e8",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3814414788",
      "sha": "23f175a72c2a27d874894d458b68ec7af51c38e8"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

