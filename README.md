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
| `latest` | `sha256:211aa06f619c622bb75a691ad0c2e1b8cc4a61d383e9f1e81bfcb66f9364c7c2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:211aa06f619c622bb75a691ad0c2e1b8cc4a61d383e9f1e81bfcb66f9364c7c2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:211aa06f619c622bb75a691ad0c2e1b8cc4a61d383e9f1e81bfcb66f9364c7c2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7403ae41f54e17c54d846872559ff653d6c22c3a",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDWBfoS9EMTAqVpqEVe6LJqIca1CScwEZm2ub0aE5OwdgIhALrea5oaC7kUZkzZaeSR5dDt716hvK+BY6SelEPkrisu",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIyZjFjMWMyNGNmYTRhN2ZlZWZmMzU5MWJjY2VhMzg2ZDZlZTFhNjhhN2UxNzZkYWI1ZDk4ZTk1NzNkNzQ2NTlkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJSEtaMDl5enFLdFFqVTN2emRkOTRwYzZ6MVVFZmpteXF6alJJZVNUcWM3eEFpQXp5aGMvaEFkcGpvcnN0UmdiN0J6SVNieVZVa0N5b0FkcFhOVWlKQzlmMnc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlJqRXdSRE5IVWk5RGQxRndjSE5FU2pSdE5Vb3lUVlpETVVRNGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVRSTlJFRjZUbFJWTkZkb1kwNU5ha2w0VFdwQk5FMUVRVEJPVkZVMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZYT1hKaFoyNUNlVFZNU21WcFRtMHZRblY2YWxsWllWQjNVRGhuZUhoeVdURllSa3NLY0ZsM1JUTldValo2YUdRMmNHRjZaSHAxUWxkSEwzZFNVRGwzUXpaNlUxWjZSa0o1WW5KTEsyaEhXWGRzUTBWc1lUWlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlU0TkZSVkNqTk1lRFozYUdvNEwwSTNNMGxYTWtzMWVrcDZWMEZKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT1JFRjZXVmRWTUUxWFdURk9SMVY0VGpKTk1VNUhVVFJPUkZrMFRucEpNVTVVYkcxYWFsa3hDazB5VVRKWmVrbDVXWHBPYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVZGt0U1dXc0tRVUZCUlVGM1FrbE5SVmxEU1ZGRWIyTnVVVkY2VVdKNEwzQm5SbVJTZVRjd1VHd3pjRFpVV0hnNVRIYzRMMXBLUVZwMGFtdFpUM04yWjBsb1FVdGlZZ3B0WjBaMmFqZFlWMjFWZERWNmEzTjNaWEZNYjJwV1IzcEZhMkpTTDFjMmFtbGhiVEUxWm13NFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxRWNtNTFiRlZyU1RoWE1ISkZURzVNTDJaS1kwWTJUR1kzVWtZeEszSlBUbXRrYldSRFpqQktjbE5OT1ZKcU4xbE5kMWxxU214NGMyZDNaelY1WjBVS1YzZEplRUZLUkRCbk56Z3daRlJ2VEdOWFZYbEZXbTExV1VKM2IxcFphazFtV0ZJdlIzWjNMME5rVWpZclRrNDNObTVDVVN0aloxTjZOblo0S3pBdllncG1NRlpQV2tFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1670459792,
          "logIndex": 8623774,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "7403ae41f54e17c54d846872559ff653d6c22c3a",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3644100315",
      "sha": "7403ae41f54e17c54d846872559ff653d6c22c3a"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

