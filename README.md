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
| `latest` | `sha256:7a1a04b2d12e725699e1213e7084397b3a23f548fde2962bf2f738779a46c688`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:7a1a04b2d12e725699e1213e7084397b3a23f548fde2962bf2f738779a46c688) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:7a1a04b2d12e725699e1213e7084397b3a23f548fde2962bf2f738779a46c688"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "58fbb3470d7880b401ce941b785b9f34136fe139",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDb50K8Q3knADN028LdobL/wblZILzNsbPJ3RsSPdk+nQIgKcHyDqU06FL3qZFy5JgrA5c+MMLqESGVcMwie8b+45w=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5YmI5ZjQ3MzQ0OWYyY2NlMTlkYWJkNjc4ZDAzODUyNjA0ZWQyMDI1NzlkZGIzZDdlZGI5MTgyYWRjMjQzZWQyIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQll2UHZuL254NzJkR2NBWFlUTDhndWtnS3U0aUU3Y21Bc2NpMkJCUEJtN0FpRUFwVEZSdERPTWJuRG5zUW9wbFRxYlVTVnNXcGg3dVZpSU9vQmJvR1llUkFZPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlUzQkNLMHBUWjJsck5HTkVVRFpCVDJoR1ExTTFZV1pPWms5emQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlhoTlJFRXdUVVJWTlZkb1kwNU5ha2w0VFdwRmVFMUVRVEZOUkZVMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZZYlhaM1ZqY3JPRGx6TkVwWmFHbFdkVXA1U2l0aU1IZE1lVzh2VXpSNVJVVk1WMlVLTVdsRVVtSXJOVWRaVWtFMFYzZGlWSGxHUW5Kc1pVdHNWVmxwTDJac1EyWkRXbWxKV1hkRWNIZGFlRlExWjJGTmFFdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZNY1hwNkNubGpjRFpxUm05UFZFWTFMMUUxY1ZrNVpGQklkSE0wZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGUFIxcHBXV3BOTUU1NlFtdE9lbWMwVFVkSk1FMUVSbXBhVkdzd1RWZEpNMDlFVm1sUFYxbDZDazVFUlhwT2JWcHNUVlJOTlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVSzI5TlRtTUtRVUZCUlVGM1FrZE5SVkZEU1VFeWNVcGtWV1Z6WVhseFRXa3lTbXBrUkRCSkszVnpkM1ZXVDFSSFQzUmtRbWhKVVhFdmVpdFJSM0JCYVVGV2QyVlRiQXA0VlVObU9XSjVTVzVDTlRsdFVtVk5SbEpOZDJ0SmQyWnZhVlZNZEdaeFJ6ZHROR0ZIUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha0V3Q25wcE4xcDNWbUl4U1VWa1NGbGFObWh5VTJwclRqbFFaek5rYW1OS04zbGtOVTh2V1Vwbk1HdG9UVlZFTmpCV2QyNTJaVEUyUkZWd1RtSkNaRlEwTkVNS1RWRkVkMU5YWjNoUlEwOW5WV1o2VG1ONE5IWnBWekJxZVVKb2RFbzFRWGMxYW01b1kwZGpVbmhMV2tkd1pta3JPV2xOYlVGWFEwUnhaM05YTTA0NVFRcFNVRGc5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670719278,
          "logIndex": 8833159,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "58fbb3470d7880b401ce941b785b9f34136fe139",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3666642470",
      "sha": "58fbb3470d7880b401ce941b785b9f34136fe139"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

