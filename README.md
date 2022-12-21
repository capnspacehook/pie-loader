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
| `latest` | `sha256:cb9a328f668feb9ca31b3481ce01df846d1652b31520913d127cc04fa37f529b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:cb9a328f668feb9ca31b3481ce01df846d1652b31520913d127cc04fa37f529b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:cb9a328f668feb9ca31b3481ce01df846d1652b31520913d127cc04fa37f529b"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "78e6e486e0d6c4ac50afab1544e2865552ba1911",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIHTrYn3rB4ylXb6oGxm+JRhF+RciSuYibDggtM/gkMIaAiEA0Zm9Fqhr8FpvyKVWxKi1TvVvdJOoUFaJcU1NQ9Hy2qg=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiMjZmYzg0ZTg2ZmIzM2I4ZWNiNDMwY2E0YmIzZGM1YWZhNGM0NzU0M2E0N2Q2OTg3OWFmOTY0ZDMwODdmZmY3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNCcXU1cm4yOU9Nd3grak85ODc5TW1nMUdMTkVsWnB4SXJmSHcvNE40bkxBSWhBT0JaYklnbzRGUHBtTVUwRnRaSHQ0U0V6VlRRZE5aaXRlYzdVbkova1JPOSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlRVTjZiMkpTTWpZeVJWWTFlWFJMZFhSalNXNUpabmxRVG5CTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1hoTlJFRjZUa1JCZUZkb1kwNU5ha2w0VFdwSmVFMUVRVEJPUkVGNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVY1ZVVobUwyVnZhWFppUjBRdmMxZFBaVGhFYkZoWGRYUkdWSE01Ynl0dGNXaHpjbEFLU1ZCd1ZrNWhhM1JIWjBodlFqazJZM2hHU2pSdWJHODRjbFJFVFZCNmFERndPRTFIZVd0YVNEQllObFZETUhRcmFqWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ4U0VWU0NuVXdTRE52UjNsTU9FOHpOVlZEY3pGM1Nsa3lNR2hGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOUFIxVXlXbFJSTkU1dFZYZGFSRnBxVGtkR2FrNVVRbWhhYlVacFRWUlZNRTVIVlhsUFJGa3hDazVVVlhsWmJVVjRUMVJGZUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWZVVkbWVIUUtRVUZCUlVGM1FrZE5SVkZEU1VSNFpWVXdSa1psTWpSNGRqaE9WR2hMY2toRmVHbDBhVEpEUjFaUWJEbEdhM0ZtV2k5amVEUmpVa0ZCYVVJd1NtUXJWd295UWpnNFpFNDJURGxaZUdsak5FTkxjRmxUTlcxMllYWXlWemhsVkRkYU0zUkRZalpMVkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha1ZCQ25NMFVGTllZVkZMU20xTWJrZzFORzlvVnpOa1JHNVhWa1ZOUlM5REsxQkdibkpoTmxWaFlWUjNUMmxyWlZSM2VtaHRLelJ6T0haMWMySXlRMDB4UW5ZS1FXcENZMmgxTUZCYWRXb3ZhM1kwYzBKbE5XdE9hbE5aY1VWV2JuUlhkRkJCTldSMlVFWnNja2RDY1ZWa1ExZEJWVEk0V1V0elpqVktjMXBLT0hKNFpBcFVXV2M5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671582868,
          "logIndex": 9515014,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "78e6e486e0d6c4ac50afab1544e2865552ba1911",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3745305458",
      "sha": "78e6e486e0d6c4ac50afab1544e2865552ba1911"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

