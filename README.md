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
| `latest` | `sha256:abce16533fe30105875860028df5779c76c81afdb8c4dc0dbd9f50969ea008ba`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:abce16533fe30105875860028df5779c76c81afdb8c4dc0dbd9f50969ea008ba) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:abce16533fe30105875860028df5779c76c81afdb8c4dc0dbd9f50969ea008ba"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "d462c351bfcf0b347ee8b1d8b1fc7e7e652398fe",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIF0r3F1KQuG36s/dJF8+8s9jpP6alEZWlkMYcJF3H3DGAiEA1z8pbguso/7yghQbtb+YTl3zEVf0OPsBwDylW/voCCY=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3Y2I0NGMxNGJhYWU0MjA1YTkxNzlkZjMyMWUwNTZkZWU0ZmMzMDUyMzQ2M2U0OWFmNmViN2U4ZmY5NjM3ZDIzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQkdoSDB3bG8rcGkxTVA1OUJxVGdibGVENmk3bG5idHptSjZjTGJ0V09aVkFpRUF3eGhTOVkyTkIrVWk0anM3RjU5Y1ZKWGJEK1FUMERVdGlqS0dsWHdYbHY0PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlVVZFJiV3cyTkVSclZtNHZORXQwVWpOVGVVZGxVWEpJV2swd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxU1hkTlJFRXdUVlJKTUZkb1kwNU5hazEzVFdwSmQwMUVRVEZOVkVrd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYxV1RkUWIza3ZhVEJKVFZkM1lWZG5NSEZJY201dWExSk1abUZ5YUU4ek5HWk9lVmtLU2xGNmNtNU1NWHBRTmxNck4zcEdVRzFuSzFGdldqUTJjR1pMVGxkRFRXaGtjamh5TTJKdGJUaEVSR0pIWkhKTVdFdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY2TVRKeENuZzROWE01YjFKcmJGbHFXSFZpYmpacFpIbHhWMk5yZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0T1JGbDVXWHBOTVUxWFNtMVpNbGwzV1dwTk1FNHlWbXhQUjBsNFdrUm9hVTFYV21wT01sVXpDbHBVV1RGTmFrMDFUMGRhYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhYzFKTFprNEtRVUZCUlVGM1FraE5SVlZEU1ZGRFdFc3dWMmRNVEVaUVVXeEthWFI2UWtWdk1TdEJNRVZoVFhKUFdERlZZVWxGUldGQk4zcHdTREpIZDBsbllUbHBRZ293UmpCUVFWSjJZVUozVDBRelZVOXpjbFpWUWtWVlJYSlpiMnhSTDJodWJ6SmxRbGQ1TVZsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2xwd0wzQkNWbGRpVFdWc09VVmFlVGt5YUVWMlNEaG9SMFZLY1d4T1ExSTNNelkzUzJSamMwcG5jWFp6WTNkSmVGZEpWV0p0WmtSRVluRXhjVFZWU21JS1FXcEJPRlJGVEhZNVQwcHlUMFE1TVZoelYxcHhZbkZXZUhCaVZtMTRjazUwV0c1RWVUbElNR3BUVTJOTmFWUXlSVVIxUVRCbWRUYzNXRU5OWkhSSWN3bzNkVms5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676853704,
          "logIndex": 13713552,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "d462c351bfcf0b347ee8b1d8b1fc7e7e652398fe",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4218962745",
      "sha": "d462c351bfcf0b347ee8b1d8b1fc7e7e652398fe"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

