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
| `latest` | `sha256:f8c32756ed9eca2181afa23d71be3db6d4fab258e3257fe206661f7749d6084b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f8c32756ed9eca2181afa23d71be3db6d4fab258e3257fe206661f7749d6084b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:f8c32756ed9eca2181afa23d71be3db6d4fab258e3257fe206661f7749d6084b"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "0be2c83b2cbd5921c60c5932c8207760480bd1e3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCYsI1S7e5wjHedItV4MqT0Xv8Wgjy4O3TwGwCofyhYVwIhAOq+vox/aWBuoGGof72T9/MSvkkXKUpdjjd1L4RQfLS9",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3NmQ3M2I5YmZkMTJjZjNiZmM0ODZiYTMxZDQyM2UyYzQ3ZWU4OTA4MWZlZjc2Y2JlNGM2Y2I5YTI0NzA1YzdlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNxeFhQd0IxTEpHaFNEVmpjYVd5VnF1dk9iK0RiRmtmMEFFU3hCUmgzd1hnSWhBTWdZc0NKcUNoNWk2QTRyZ0ZDZVc3ZWhIb3gxTG41andwdDBBcXZnY1JyRSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlRHNW9Nalp3TDJSdGVVWlRZWFV4YUdOTllrVnphWFJvVTB4RmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlRGTlJFRjZUMVJCTlZkb1kwNU5ha2w0VFdwRk1VMUVRVEJQVkVFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZhZURoeFJWZ3hNRkZoZDNjMFkxRnNSbFpRTTFka1dEWk9WM0F2V2poRU9ERk9ZWEFLZUVwUWRtTjBkbUZ6VjFSYVNYRlpaVTFOTjNWWFZtTlBUMk4yYkVkcFZIVmlVM2hxUzJsTE1rODJWbTl4Wm1keFUyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZUUVhSTENrNU9USGRhZWpaM1pXcHlhakpOVkRoTVRrZG5WVkJaZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkWmJWVjVXWHBuZWxscVNtcFpiVkV4VDFSSmVGbDZXWGRaZWxVMVRYcEthazlFU1hkT2VtTXlDazFFVVRSTlIwcHJUVmRWZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWVkU5SlYwOEtRVUZCUlVGM1FraE5SVlZEU1ZGRFMwMHZObEJtVGtGWFR6UlBhV1pRVkRaME9HcFFlRFJsVVhaaVkweFdSVTVQYTFsVllsWmlTbmhNVVVsblZqbDFiQXBhTTFWNVF6Z3ZWbFo0Tkdaak1ubzRURTVpYlhwRlFXcHFVR1JUWWxaMmFqRnBlRmcyVERoM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xCNVozSndORVpTU1VwdlVHWkNlRGs0VW1Fek5FVkNiRmxFYUhsS1dWcDRhbmg1Tmt4b1dURm5kR1pqVkhNNFUzQkxiMGM1VjJoM2N6TjFhR1J3ZGtrS1FXcENVVU5EVmtGNVN6ZDFLMjlTZVV3MlRYVXdjRXQxVERScVNYSlRWV0ZpVVV4cE0xbFpUSGRZWWtGalZGYzRaM0J2V1c5Q1FqUlNjMlpwVUZsblZRcERURlU5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671064774,
          "logIndex": 9113420,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "0be2c83b2cbd5921c60c5932c8207760480bd1e3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3699969457",
      "sha": "0be2c83b2cbd5921c60c5932c8207760480bd1e3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

