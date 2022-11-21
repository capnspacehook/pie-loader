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
| `latest` | `sha256:0eb6457a71193e6c5cd17ffd17fcf96fd8807e7a2cd888bf3089591b5ebadcc6`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:0eb6457a71193e6c5cd17ffd17fcf96fd8807e7a2cd888bf3089591b5ebadcc6) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:0eb6457a71193e6c5cd17ffd17fcf96fd8807e7a2cd888bf3089591b5ebadcc6"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "af3253abd6fddc2c474e940e6ee23252d48b893e",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCJ/Av1Kv51waE4z/mMyMaevQeQeW2fqtHcvjqGRun3SwIhANE/1tjyQlVjGr3B3hUSNuCejad22bb2UBPOE8c0Swi8",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzOWU1NmEyZTA2MTgzNTI3ODM0MTYzNmY1NGE2MjM5ZDdiNWRjNDY1ZmI0MWE3OWIwNjE0YzI0MzM2ZDQ0MDNmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNZaExZQjJTK3d4MzNFSC85dG51YmZIN1paYTVDbXM2dG8rUCtFUCtZbnlBSWhBSzg2S2R4cGQvb2JaU053QXZ6VFpsWnBQeHpPTHc2bHJBcFAxOEx5RWFQTiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlJUaDROR1pKVG5WbVVtMDNlbUYzU1dsbGRqSjNkVTUzVDFKM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1hoTlJFRXdUV3BWTTFkb1kwNU5ha2w0VFZSSmVFMUVRVEZOYWxVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZvUkZwQ1YxZFFaVVpSVVV3dlRHdFVXVFZDTjB4c1ZtZERLMGd6VUdaUlVUaEllV0lLUWxsbVRYSlJlVWRRZWtkSWEzZFpiVGRVUjNSaUwzQXJaWEZXTTFabVZIUkZZekpqSzNCbVVtUjBlR05FUjFOelZEWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZTYVdsbUNqVkROMGd6Tkhwa1RGZ3JSRVZXUkdWS1RYbEpkelJ6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdoYWFrMTVUbFJPYUZsdFVUSmFiVkpyV1hwS2FrNUVZekJhVkdzd1RVZFZNbHBYVlhsTmVra3hDazF0VVRCUFIwazBUMVJPYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUV0c4eE4yd0tRVUZCUlVGM1FraE5SVlZEU1ZGRFIyMXZXSEphVDBSUkx6ZEdNVlJIZWtKYVVVY3hjREpsV0hBekx6ZFJTbVUzT1hOd0wwRldMMlV6VVVsblJuRlhUUXA1WVM4eFVGRk1NSGhSY0d4aGVVc3plWG95SzBWRFJGSlBaM2d3YTJGSllrMVRibHBHZFhkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTGNUZ3lOREkzYjFOSFdscFdVWFZ6YUdoTFZEUktNMmxGU0dWMVpGbG9iVkFyTm5Wb0swZGxXbVpYUmt3MmJrZFdaeXREVWt0Rk4yZzFjelpwYkdVS1QwRkpkMU15VVVRMGJVWnhOakZJUldsVE9GcFNaMGxtUkhCbloyZzRSQzlzZEhsc2JrWnRNbHBUZGsxS1IwWlpSbWMxV1c5S2ExTm9SbFpSVkVWNFJRb3JXbXhyQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668991398,
          "logIndex": 7506489,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "af3253abd6fddc2c474e940e6ee23252d48b893e",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3510516348",
      "sha": "af3253abd6fddc2c474e940e6ee23252d48b893e"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

