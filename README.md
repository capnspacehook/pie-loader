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
| `latest` | `sha256:f8c4f3fed298dfd5f3c5ca204134e74fe54b87f50e2e2045c73d6ffeed25ffbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f8c4f3fed298dfd5f3c5ca204134e74fe54b87f50e2e2045c73d6ffeed25ffbf) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:f8c4f3fed298dfd5f3c5ca204134e74fe54b87f50e2e2045c73d6ffeed25ffbf"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "d8da2ee14b20131ad20fca3132b50d5fd2b726fb",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQD8jpF75UdqiPAxi3Y/5tG1LfWjY+o2DHuOPUk0aS0xRwIhAMjU3njfCpxLj5vi0ehVT9RW5x9yPacj4pgntrTSCfGB",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwOGEyZWJkZDg0YWZmMTI4NjE3YWVmZTc5N2M5NDBjY2UyNmYxMTRkYTYxNDRjNTYyNjhiZmIzZWYzZDAwOTkyIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJR1BVQVUyQTJkbk8xcmdlT1M5alpRci9xdmRNK3k2Y3JacFNkMnVOcmJmckFpRUFqdW1lK21vTW5NUXNFWjBJcVdHejlTNlIxUHRWZDR6ZE9Eb2xGYkIrYmNrPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlJWQnlRVWh2Y21kbmRVMW1ibE12TDNSaVEzaG5MMmxtTDFaWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVRSTlJFRjZUbnBWZDFkb1kwNU5hazEzVFdwQk5FMUVRVEJPZWxWM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZNTlU1dWREVnRla2RyU2pOMmFrcFphSFpaZURCdVdFMU9ZazAwV25wcmIyYzNOaXNLVEdZdlMyZFJiVGhpYUZSdlowNU1kVzVXYTJ4Q05rVmhlVTkxV0ZaWlNYbzRiVGxqVmk5SGJXazJlV1ZPVFZaMmVUWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMWjJSM0NrOU9lWEU1YldoUUsyaHdlSEZoY1hoR1NGTXhWRlpyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0UFIxSm9UVzFXYkUxVVVtbE5ha0Y0VFhwR2FGcEVTWGRhYlU1b1RYcEZlazF0U1RGTlIxRXhDbHB0VVhsWmFtTjVUbTFhYVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaZFdSU1Uyd0tRVUZCUlVGM1FraE5SVlZEU1ZGRGJsTnJRMmRPYXpCRWJGTnVWRGhxUlhSMVMwcEdWRnBNUlRsU1VrOVRXVXN2YldVeVdISnZXVnBTWjBsbllqWllOd3BTU20weFVFRk9aM2hqTkU5cllXcFFOM2xpYVhSck1VMUlTVEJrSzJ3clUzUlRWSE5oVldkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xwemJIVXpjRmszVmxOMUwwSnFia1ZpTnpsdWQySXhha1pzZFRscWFUVk1Ua2hVUnpKd2RIWTNaRmRWT1ZCc05UTnZlVEptZURaaE4yY3ZWVGxqZGtzS1FXcENkMGw2ZUUxR04xaEpVa1ZZV1ZoelIycERPV2ROZERJdk5GUjRXaXRVVlVSMmJtOVlWMFZCWlZKWGRVUnNkRTVFVmpCVU5qVk5TR0pCZDFsaVZncFpNVFE5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675816696,
          "logIndex": 12858844,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "d8da2ee14b20131ad20fca3132b50d5fd2b726fb",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4119588977",
      "sha": "d8da2ee14b20131ad20fca3132b50d5fd2b726fb"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

