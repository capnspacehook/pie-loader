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
| `latest` | `sha256:006daa030b6722ebdaaf4ef54055a4798257bfeb8e244dcdf013fea93532a12f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:006daa030b6722ebdaaf4ef54055a4798257bfeb8e244dcdf013fea93532a12f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:006daa030b6722ebdaaf4ef54055a4798257bfeb8e244dcdf013fea93532a12f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "56c7f9ef8b42da2b2b796807bcec90703d7ab0be",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQD8l7jzjEgISQnA0lZtfFks+WgrpRvu1oqWHsyV1qRCDwIhALSKuKTX85/qzrXe4N8J9oediBqQYAfdQfQKBIQLHoro",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmYmVhZWFkMzI1MGMzNzU5ZTFlMGExOGFlMzM1ODA0MjJlYzViNjE1MThlM2RmNTVlOGY3MWY1MDI1Y2U2M2NjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNxT3o0ZE1oY291YzRYRW0yMnlQUkdyeDlQR1RUbEppc0FqOElTaXAybk5RSWdldmp2aHU0dExHVXdJN3NVaFFQWkkwWm1mQVlHamtTUDVTOTY2K0dyRG44PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVldHaHRTR2RGVkRRNVFtWkJkWHBJYjJReFMwVnRielJsVEhKM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVhoTlJFRXdUWHBSZVZkb1kwNU5ha2w0VFdwQmVFMUVRVEZOZWxGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZIUVU1WVJEQnpXWHBIY1c5dlZtZDNkM1JsUkVWTU1uUkNkbTlJVmk5R01GWlpNRllLYjAxdmFXVTFiMlpTYUdSa1dsQnpUMU54ZGt0RGIzRk5WR0ZYUlVsTGJqWnliMk5JY3l0cGRUbFVielJNYzBaQmJ6WlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMTDFwR0NtVlphWHBNTTJwMlNWQTNSR2xzY3pOVFVVWXZhMmhCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGT2JVMHpXbXBzYkZwcWFHbE9SRXByV1ZSS2FVMXRTVE5QVkZrMFRVUmthVmt5Vm1wUFZFRXpDazFFVG10T01rWnBUVWRLYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVVEVrMllXOEtRVUZCUlVGM1FraE5SVlZEU1ZGRVpISXlZVFJhVDFsS1ZqY3djeTkyTDJOeGJVbE5TVlpxTkdZNVZGQmFUSFkyTkhKS2RHWkVUMk0wWjBsblRWaDJOZ3BrWVVKTE9XUlNhVkYyVjFWeVRVWkxWbGhuWTFOT2IzZFlhSHBHU0hOck9GSkpkM0l3YW5kM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGTlNFZG1hREJTT1ZOVFQwdDJhM2cyVG0wM2NFNTNWRXBaUnlzd1dVOVhkWEo0WmtRNFFpOUJZbnAxVjI5VVZEQlFZbkJrVjBreVpYQkdZVFExTjFrS1kyZEplRUZQU25ka0syeFRiazU2YldKU1JEQTViRFprSzBKVFFtTlVNbGt3Y0hkamVFaHNPQzlrV1RKTFVEUjFla3d6ZFdkb05FUlNVQ3R5ZVdvemRRcHVNRU5oVTNjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1669855443,
          "logIndex": 8190080,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "56c7f9ef8b42da2b2b796807bcec90703d7ab0be",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3588351761",
      "sha": "56c7f9ef8b42da2b2b796807bcec90703d7ab0be"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

