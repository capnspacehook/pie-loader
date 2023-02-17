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
| `latest` | `sha256:972a26d1eaaf1701318feed186e9ca761d8533390709602ce0298d685c903966`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:972a26d1eaaf1701318feed186e9ca761d8533390709602ce0298d685c903966) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:972a26d1eaaf1701318feed186e9ca761d8533390709602ce0298d685c903966"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f2099213b7c24745c5a4338d6bf2bfe312aef5d3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDH1f3HgZFH29AVWTFEC/H24Ja+VWxkmzztPl5kRYbpIgIhAKvi7zVtP5c+HThHRHGf9tsgKuHniBS1k88TGo6PAt8T",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhNTNlMjgxZWEzMTNjYzU3MDMxZjhjMTJjMDlkNTk2NGEyZWU5ZWViMjJmODhiZmNkYTU4N2MzYTZmZDc1MTQ4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURHV0pHTzJBdzFtNE8rT2hUSHRzV3hnbTBraXNKWVpMOEZZN3VxbGN5Y2VnSWdIZ2hqMzdkMWplSTRaVjZHcVVnd3BrRzlZWWcrTndtQzFWY2cxOEFEZjZFPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlEwbGpVbUZhV1VkdFJsVkNOMmRxY1V0blR6UkRkRTQxUWt4WmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlROTlJFRXdUV3BGZUZkb1kwNU5hazEzVFdwRk0wMUVRVEZOYWtWNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVVyVDFVM09GWkJWMEY0VEhKU2EzTk5lV1F2TkhCUGRtWkJZVlpqU2tGTlVEZFJTa2NLVVROVWIzbG1LMVI2YmpScFdHcHNSVTkzVWl0WVZXaHdXbXRaVUdNM2VYUm9VM0ZEZUhoVWRVbGtZWFYzVjNFd1FtRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZvTUVkSUNrTmlORkZvUTI1SVpuSnpNMlJuTjFSVWFWUlJkMDlCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxTmFrRTFUMVJKZUUweVNUTlpla2t3VG5wUk1WbDZWbWhPUkUxNlQwZFJNbGx0V1hsWmJWcHNDazE2UlhsWlYxWnRUbGRSZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhWXpCck1FSUtRVUZCUlVGM1FraE5SVlZEU1VONmJUVldOSEZqUjBFeVFrTlVSR0l5Vm5WSU9XeEtRWHBLVWpCU2FGQmpSUzlTTDNWbmFWaFlXV1pCYVVWQmNFSk9jQXB3ZWtjMFQxbzJXVlJ2VldSUlpVZEhXbTlJY1VNNGVGRXhOMVJQYzA4NGNHeEphVVZoZEdOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2xsc1RsTkViRmwyT0hOck9YcFFWaTloVFRWSlFrNXphVGd5UVZwblFUZzJkVEkxTlhwWVJIUjZaRUZOYzNOR2VtNXVjVmx4UjJ4clUzWnVRek5sYjFrS1FXcEZRVFprTkhvd2FsbEVhbFp5TVhORGEyeG9RVXMwZFdWTVExWktaR0pEU0hCVWMwY3pNVWhRWVVkUWVGcDJhV0pYT1ZSeE4yWTJTM2d5VlRSRlV3cDBieTlVQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676594553,
          "logIndex": 13514142,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f2099213b7c24745c5a4338d6bf2bfe312aef5d3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4199531216",
      "sha": "f2099213b7c24745c5a4338d6bf2bfe312aef5d3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

