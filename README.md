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
| `latest` | `sha256:c2e16b244878366102a7d5a50a5c1ff9029724ac7c90eb7346df7d63882bb5d8`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c2e16b244878366102a7d5a50a5c1ff9029724ac7c90eb7346df7d63882bb5d8) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:c2e16b244878366102a7d5a50a5c1ff9029724ac7c90eb7346df7d63882bb5d8"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "6eccb988123e6efb8b4d2df1bd9a5f6aaca24200",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDYIYojiTdAB8fKRfybdjUpUEDdY7biqzmfJiHZLr1ZBQIgbz57oZhSLjyNfWUYF1CR+Ypaqc3t0cRRqS/FJXtiJfA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjNTNjMDRhYWMxNDUyMTQ1YzUxNTFiNWQyNTAxZTk1ZjM0ZDU0N2QwN2NhNTAyODNkNDNkOWU5MmQ1YzkxNmYwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUR0UXhTOFg3ck5yTThxWkxYTzRiN0diRFF5ZG96NjhObUdPY0kyQTJLYVBRSWhBSXpvKzZiWHMxUVdKZTRVcWtVd055VWV1WWNvc2kvTENSLy9lTEVQc0NIYSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlQyeGxVRmg1UkZWWFIyWjFMM0pQYUcxTGJHTnFiV2x5ZFROQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRWTlJFRXdUWHBWTUZkb1kwNU5ha2w0VFZSRk5VMUVRVEZOZWxVd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVVyV2xoTE0xRkhXa3hsU0VoV2VEa3laMEl6U1VsNVNpOXFXRVJMYnl0UllTOXZjVVVLZUdGVUt6YzROM1JUYTNGYU9VcGFSekZ6ZG5ZMlMydFZUWGRoZFdKSFNHdDZjR1kzYVVOeFdqTTJTbTlPUmtWQ05qWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlU0VFU5b0NtWm1hRFYxVWsxNVQzZExXbUZWY2xVd1NXOUxkVzVGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpKYVYwNXFXV3ByTkU5RVJYbE5NbFV5V2xkYWFVOUhTVEJhUkVwcldtcEdhVnBFYkdoT1Yxa3lDbGxYUm1wWlZFa3dUV3BCZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUVGxZMFoyd0tRVUZCUlVGM1FraE5SVlZEU1VNeU5FMVFlRUpOV0U1eVpXNUdUM0Y2YmpSaUt5OVNMMUZpVnpsYU9HZHlRMjh3U1RGRWJUZFpha1JCYVVWQmVuWllVd3BxU1hkV1pGWlFUWEpUSzJZeVREbG9aMEZ6YkVvM1YzcHBTbmxKWlhsYVdHMUhXVTFITW1kM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGTE5FOTZPRUZwUkdoTlFVWlhjV042Umt4MFRFMUhSV1ZRV2psVWRXOUJVbTlaT1cwMFVIaFpUMkptSzBWaFpqbFZhRWw0YTNRd1R6WXhNbmwxUVVFS1VtZEplRUZQVEhNcmRXOVdTRFJEUldsT1ZVZ3hjR3BXVm1KclJtaE1LMHQyUkVGWVpYWjVTQ3RMYldGT05scDRMMDFDWTAwMlIxTllSVWg1VkZCVVZncDJOemwwTVhjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1668818667,
          "logIndex": 7382404,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "6eccb988123e6efb8b4d2df1bd9a5f6aaca24200",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3501283579",
      "sha": "6eccb988123e6efb8b4d2df1bd9a5f6aaca24200"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

