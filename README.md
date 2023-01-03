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
| `latest` | `sha256:97bd6789d9748713a8a801471d752096efc11773f249354a660a72affe9571b6`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:97bd6789d9748713a8a801471d752096efc11773f249354a660a72affe9571b6) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:97bd6789d9748713a8a801471d752096efc11773f249354a660a72affe9571b6"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "9fd3366f37a14a0dcdf433297880eaa3259a9c92",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIAObGs5Y8MybgOaSPCFvxpu+7axoxYFHSbS/+VRU6t+FAiBEK+7sMeroLSjfrncInvHgXOC2lhgVDXi3W0w5pPMQJA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiY2JlNmFlMzNjYzRmOTI4NDI4YjNkMjRhODU1MDZjNTg2NzU0YTU0ODE1NzgwNWExZDA4Y2M1M2M5M2IxZmQ1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNwb296UHF4ZVlwcEpWTEczbVZsSURZSTY0OGVvTjFUQ2E2M1NRc2xYTFBRSWhBSW54dEZ3OHNzcm5MaUFqNS9HSG5sdTFVRWlNdlVpZjJQQzVlQU80Um02dCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNWRU5EUVRCaFowRjNTVUpCWjBsVlRtSk5hR05KTTNWcE9EQTBTakpLVTJWdE1tRXdWV3hDT0RCdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVhwTlJFRjZUbXBGZWxkb1kwNU5hazEzVFZSQmVrMUVRVEJPYWtWNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZoTVhSV1dGbzRlVmsxVUc1alYyRnBOVU5VVFVWa1RtbzJlVmt6Wml0QlVGaGlZbTRLVW05UlRraHdaMGc0VVZGVVNrbHljMEY0VEdSMmMzZEdOVVpMVWpoU01HNXZObFJSY25OTFMwWjBTRE52T0cxdlFtRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ1YnpVdkNuQk1URE51S3pGT2ExaGpSVTFFZWpsSVkyRXdRV1pqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWYWJWRjZUWHBaTWxwcVRUTlpWRVV3V1ZSQ2Exa3lVbTFPUkUxNlRXcHJNMDlFWjNkYVYwWm9DazE2U1RGUFYwVTFXWHByZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXTVVSeGMza0tRVUZCUlVGM1FrbE5SVmxEU1ZGRU1FaGhNVlpLWjFBNGVFUmFNMUZ5VTAxaU5ISktMelV3VG0xSlNubHBWbVkyVEhwU2NXeDRVVlpTWjBsb1FVdHBaQXBGTlZSaVJUbHBibGx4YWsxUWVtWjBiMngxWW5NeWJHa3lZMHBPWnpJck9GWTBRelowY2tGR1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeWEwRk5SMWxEQ2sxUlJFaHlkek5pUzFseWJ6WmxhRXBQWjBoWlJFOUhXbE5SYzFZMVFYRXlWa1p6WVZnMGIycHlORE5wWVRWcFJEUnBUVEZMWTJWNmNVNVZVaXNyWVc0S1FVbDNRMDFSUkVScVEzaE5lWEpVVjJOTVEzcDVRbGcyUjNoaWVIb3ZaSFJ0UWxGeVZHdEphaTlHTjA1R2QxZElWM053VUZsWWFVbExRVzl4YVdzM1FncE5aamh1UzNWSlBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1672706195,
          "logIndex": 10357315,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "9fd3366f37a14a0dcdf433297880eaa3259a9c92",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3825956345",
      "sha": "9fd3366f37a14a0dcdf433297880eaa3259a9c92"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

