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
| `latest` | `sha256:ed5b4619458bdcbf43db5a22067c51afab3a4ad83fb32998c172723a513f0e5a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ed5b4619458bdcbf43db5a22067c51afab3a4ad83fb32998c172723a513f0e5a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:ed5b4619458bdcbf43db5a22067c51afab3a4ad83fb32998c172723a513f0e5a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4f33f62e991d92092064858b7bc8bca747a4abb4",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIAikiBanxf1HeOw+AdQEnYHdeg8UZ63hZNk+Hg87U06sAiEA31mBJSkpwQ82JEbJfTm3NBg/4GkvTjzH5TTPzCZcoTI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhMWNlOGQ4NTY5NWE4NjExODRkNWI0MTgxZWE1ODkxNDY0MGY2YTZjMjAyMjg2NzJlNzU3YjYxYzNlOTExMDdlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNJU28zVktBdU1tQmlzalFVZ1JzK1plRmMyaWpSQVF5L1FJZVVkb2E5emtBSWdhM0NIazFHTUE4ZnhHZTR5VWpBRkhsZjZ1SHEwRTJpc1FYVTlhWFVPamNZPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlZreDFUWE5pY0VFMmRFeEhaRmxOTjJkRk5rMU1lVU42UzAxbmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVRGTlJFRjZUMFJGTWxkb1kwNU5hazEzVFZSQk1VMUVRVEJQUkVVeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUZWxJclFsWjZhWEo1TWl0aFRGVlBZVTkwT1Rjek0zUlRPV3hIWWtzNGJrTkRPRzBLSzBwVWEzcG5abFJhYVhaVFprWTFlRUZDZUU1UVVGRmpOREJ2WWt0RmFsaDFZMHc1WlVsNVNYWnRTa1J1TTFod2R6WlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMVkRNd0NrbHBXbE5MSzFablpsVnplRk5EUlZRMWVEUTBZbHB6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCYWFrMTZXbXBaZVZwVWF6Vk5WMUUxVFdwQk5VMXFRVEpPUkdjeFQwZEpNMWx0VFRSWmJVNW9DazU2VVROWlZGSm9XVzFKTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXTDFoVlNXc0tRVUZCUlVGM1FraE5SVlZEU1ZGRVRUTTNkRWhRWjJSalRtMVZSakZrYTJSMVRXTXZTbFJ3UzFwbWIzY3pRV2h0ZEhCdGIxUkliVnBZZDBsblVFUlZhUXBJWWpabU1GZ3ZNR1kwWXpOYU5ucFFhVGRqZWxwcGNuRXZaRkJJZVZWc2FtOHZiM0k1V1VsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGUE1qQjVXRGMxYlV3dmJrWklhek5OYWpCV1RGSXlTRkJMYjBGSE5tUjZXamhrUVU1QkswNVFORTFpYWxSaE1HVkVUak4wZDNkeFprbDFlRGhpWmtNS2IzZEpkMHRYZUhSdVpVSXJhMVF6YW5ZeFowcFZWR2RsYkVWUU4wZFpiREpVUjJGbFV6TXljelk1V0ZCNE5saFFSbEJ1WVM5TFEwWlBZVWRuZGtNMFJRb3phVEZaQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1672879120,
          "logIndex": 10490183,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "4f33f62e991d92092064858b7bc8bca747a4abb4",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3842792406",
      "sha": "4f33f62e991d92092064858b7bc8bca747a4abb4"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

