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
| `latest` | `sha256:482542d4c242a127e5b5f51ad83e0165169d27e9cf5c20bb3ed8206926744a73`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:482542d4c242a127e5b5f51ad83e0165169d27e9cf5c20bb3ed8206926744a73) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:482542d4c242a127e5b5f51ad83e0165169d27e9cf5c20bb3ed8206926744a73"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "198e1adcf2d507cfd35c2a122867b6ddf07d2897",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIGXhsL6l0Qjqz1WUToyvpaEh23S2JnDMpe4Zw/nPsIXmAiBPDKaRtDZwq5DnUtJaEfz0jDeOYmNdDEEezfbIM8GJZw==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1YjYwZGI1N2EzMTA0NWQzN2MxNTFjNzNlZDZiYmFiZmQ1ZWRjM2IwZDY5NTI4NjEyM2I4ZjNlYmMzNDRmODBjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURuTnRqNHpsN1g0ZDZucDJWSXVCMSt1dXFTV0Erb01VT1Ird0VPV3RWSGxRSWdEMFhORGsyRlFIYnVJeGlZbUwvTHJTTU1wcHprUk00em5LZkNDdS9TYVNJPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlNXbExkVTFpZEcxSE1HRlRlRVJ5VEVkQlpFbFpRa295VUhWbmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVVFhoTlJFRjZUMVJWTTFkb1kwNU5hazEzVFZSTmVFMUVRVEJQVkZVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZRVTBscGJrTkJkVlJEY1hwbGVVWmxNa3BRYjNGellVdDJSRUoyVWxKelJWRmtlWElLWW1FdllVRkNWV3BrVjBWcmVYZzRlbXMyYVM4d1RFZ3ZLemxXV2xaNVVYaG1UakYyT0hSUWFXMHhhaTlXVVdWVFRUWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZOTWt4MkNuaFRURnBHWm1ZcmRtdFhiMGR3Y0N0VmNVWlJVRE5yZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoUFZHaHNUVmRHYTFreVdYbGFSRlYzVGpKT2JWcEVUVEZaZWtwb1RWUkplVTlFV1ROWmFscHJDbHBIV1hkT01sRjVUMFJyTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaUmxKRFltRUtRVUZCUlVGM1FraE5SVlZEU1VKYU5sazRhRTR6VFRkc1ZVZEpSMjl5VUdvMk1sbDRVMkl6U2xWaWMxVm1Ra2hFYjJ4V2VFWlJkRVJCYVVWQmIxRXJTUXBoV1c5V1JpOVlMMDF3VEU4clNqTjBSVWh5Tm1RMFJrOUZPVUo2T0d0TWVUZE5aRkpFTjFsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2tkbGIzVkhPVkJSWkVSM2JFVndRVlpwTmpWdVlWZGpTR2xIWjNKTFQzUnNjVWhZVjNCSFlsbHZjWEpaVVV4VGVuUnlhVFpxSzBad1RFbFdRMGxoVVVjS1FXcEZRVE0xUWtWTGFXbGpTR3hMTWs5dGRYSmtSRU5TU3pWSWNpOUhibU53Y1ZwTk5sVmljV05LVmtWR05sbGhObXN4Yld4bGJETjVPRXAyT0c4eE53cHhiVGsyQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675125620,
          "logIndex": 12299103,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "198e1adcf2d507cfd35c2a122867b6ddf07d2897",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4049550874",
      "sha": "198e1adcf2d507cfd35c2a122867b6ddf07d2897"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

