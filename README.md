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
| `latest` | `sha256:e9b2fc32bdd374598dd0c31e75e8f2c5b214399b4caaacaab622cf58e1fba287`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:e9b2fc32bdd374598dd0c31e75e8f2c5b214399b4caaacaab622cf58e1fba287) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:e9b2fc32bdd374598dd0c31e75e8f2c5b214399b4caaacaab622cf58e1fba287"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "8aa114ea74f28ff597fb2b16c3a70f693da11d3f",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDY45Ux1sJtuDGP4wnwk8Ujr1tTnoxif5Zr0u5OPFd/iAIgZ/Lomo4j4+gK5S2v12CefxIyphVZuatCsfBGDyg4YzU=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjZmY5MDhhYzg5ZmYxMWZlZTcyY2U1NmJiMmU5NmNmMzVmYzMwMWEzZDExYmNmMjFiZjE2NTY4NmE3ZWJjZjMzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQm5YODh3REkySkprKzZ1cU1RSkdOdVZXUVM0eWdmZ0JSRFAwTktmbnR4SEFpRUFyZ3pjRDlSM3dvenc3S2FObHZ3UlpjVHdpT3NXb01IanN5ZFovYmt5Z0FRPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVllXOUROR2x1T0RWUk9VdGxaak5VT0VOVmFtVXZWamt6U2pGcmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRSTlJFRXdUbXBGTWxkb1kwNU5ha2w0VFZSRk5FMUVRVEZPYWtVeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUwZEZsTlN5OWFhbkZrTWk5VVZYTmFMM2x1Y2xoTmRTc3JNbHBtYVhFNVRUWk9lRkVLTVdsUlYzRkRTR1ZzV0ROQmFqWndOSGcxVlM5V1VIRk5ZWFpxWXpZelFtbGFkbEJQZFZKclJFUlpWMUF5TW04MlZXRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZRU0hWV0NqRm1abFJJVERWSWVsQlhiMk0zVnpOalFXUnZaSHBqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpSWlYwVjRUVlJTYkZsVVl6QmFha2swV20xWk1VOVVaRzFaYWtwcFRWUmFhazB5UlROTlIxa3lDazlVVG10WlZFVjRXa1JPYlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUU1UweFZFVUtRVUZCUlVGM1FraE5SVlZEU1VWd1IxZFlSM1ZVV1hoVFNUWnJjRGt6TDI1UGJXdFVLMFUwUVZVMVVUQjVOMWh6WlRCVk5rVldlSGhCYVVWQmFsZ3ZhZ29yY1ZCRE56bGlWMlJPVTIxRVZEazRWalZEUjJwbmJIb3hNREJhTVZoRlkzazJMMEZTV1ZsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGTFVVaElLMWxEVGpGck16RkVSM05XVlRaaGVqWnBPSFY0UVVGeFFrSk5SQ3RVVFdKNlJVOTRSbU5pZGsxd1dtRkRORFEyUVRGMEswRndaVGwwTkdvS05GRkplRUZMTlhSbE9HdFZMMEpaVFVWNFVtcHFkMVJIT1RkM1ZXSTVLM0ZhTkVsbFEwRjBjbFZTVTA0d00yeFlhM3BMVlVjM05reDRaV0owZFVndllncFhiRlJ2VW1jOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1668732400,
          "logIndex": 7309483,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "8aa114ea74f28ff597fb2b16c3a70f693da11d3f",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3493222959",
      "sha": "8aa114ea74f28ff597fb2b16c3a70f693da11d3f"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

