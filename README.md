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
| `latest` | `sha256:6c88898f4d56e96e33625df525da3c3348c3e9951ad23c91e5425bb0f34a11d1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6c88898f4d56e96e33625df525da3c3348c3e9951ad23c91e5425bb0f34a11d1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:6c88898f4d56e96e33625df525da3c3348c3e9951ad23c91e5425bb0f34a11d1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "19c42c72622867ed1f3d56997999c1d9374d6698",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIFtwGMcWFcStSC8t+0PY/zvX3BUqrvXMdM4aD9WbEFLZAiB0lFCa8ajLmogNTCejVFVRDV1/APvig4FEDUJxS8wMoA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJkZjE5OTNkMzNmNGRhN2RlZWI5YzA0NWYxYTgwOGJhNTllMzVkMjJjMThjMjQ4ZDI3NzEwMDJmZjBmZDg4MzFlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUREcHBPTjVDeStyWjNEU2FpNXN1MXBEaitsaFRsZ1hHUk1WZWlQdHpKT0tBSWhBTGY0OFNWeHFzanZGVGJSdm4rSWdjTHJYQUplclZ1WkUrZGlrb25yd2RJTyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlVFZElWSFJqVUdnckx6WTNWbkpMYldkTGFqZHFjRFZrTlVaQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlhsTlJFRXdUbXBOZDFkb1kwNU5ha2w0VFZSRmVVMUVRVEZPYWsxM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV6VHpGRVVFWjVkazVtUVhsMVpYUjFVU3M0TUVSdlRXTjRlV3BXTkVObVZuVktWbWNLV21waVIzSkNiMGxHUjFkSVVHNHpWWGxQZFZscFZqWjJjREkyYlRaRU1FZHJSazFhVGtweWIxcERSM2xwVGpCdmJtRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyUkRoR0NsWTRkbEk0YVV0SFIwcGFXR1pIVUdoVFFqTnBjRkpGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoUFYwMHdUVzFOTTAxcVdYbE5hbWN5VGpKV2EwMVhXWHBhUkZVeVQxUnJNMDlVYXpWWmVrWnJDazlVVFROT1IxRXlUbXByTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTY0ZSWFQzY0tRVUZCUlVGM1FrZE5SVkZEU1VaTWIzTkVSV3RRUkc4dk1sYzNSMkpIZG0weVR6WjFNR3B2UmxWUFFtUmlVR2sxUm5SWVZXRkhOM0pCYVVGQk16ZGllQXBDZUhka2FFd3ZNa3hHYTBkcU1YaHpaRXhtUmtNclYzVnlPVVI0T0RselNFWnBjbVZJYWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ25rMVNVaHZSbWQzWmtKUU1ESkRibTF4YVZvMU5TdEJZek5xYkN0SU5qRlllVXRWTVdGUVltNUVkRWRoSzBGcGFXOW5iR013TDNKMlQzUTJiVE5sV2pRS1FXcEZRVEV4UTB0aUx6VXhOM1ZqZVRSbmJtUXZlV2t5TWtsVFlscFVWbGhFYmpkbGJIbHJVbTVDVFc1aVNVZFNZMlpaV2pKNmJYRm5ZbmhoUm10V1JBcG5jbW8zQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668214022,
          "logIndex": 6903277,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "19c42c72622867ed1f3d56997999c1d9374d6698",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3448885101",
      "sha": "19c42c72622867ed1f3d56997999c1d9374d6698"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

