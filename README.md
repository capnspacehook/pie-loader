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
| `latest` | `sha256:93a92d765bab78deb42037030a5b930a9f9051248f4721eff3ae1038b095e3c1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:93a92d765bab78deb42037030a5b930a9f9051248f4721eff3ae1038b095e3c1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:93a92d765bab78deb42037030a5b930a9f9051248f4721eff3ae1038b095e3c1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "756ae0f5a2470a75c4ec245015d1aeaa583f6a64",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCaUAtp0x9ruLdA2JP514dNczc0GrELERhyeT+B1SQtJAIgOMw523//eByckBrs0XeIGUhRL+S8EWmjfFX8lptJyOA=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1NWRlMmFlYWYzNmQwMzdmYWIzMTczMDA4NmUwZjBhYmMxN2IwYTA3NmQxOTgyNDQwZDBkZmY4MmQ4OTZkNzdjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUURmQjFCRVIrTEsrNzEzRksrOER0SFVjNkVYTXExWmx3YjNjY203OEZsRWtRSWdab0hMUjY0VUEwdVFlUVNQdGNHMk1sWmMwSVpvWjdpYjVDZkUyMnI2c0xFPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlJXdHNkMjVKUVc1NUszVnhhWEJFVWxGQ2MzazJiMnRuWkdkamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlhwTlJFRXdUVlJKTWxkb1kwNU5ha2w0VFZSRmVrMUVRVEZOVkVreVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV6Vld4ME9UZG1VMDFhTUZscWNHcFBMMWt2WkROVlltd3ZabkZzTHpsclFXMXRNV01LVHpaRmNYWk5WRUV6YkN0RFZXSkplRmxLUW5sVVdrVlhWeXRsTkZadWJGSktRbWt6UW10dFNHNXNRVGRoU0RadmVuRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyY1ZCdUNqTTNOMnBIT0haUmVGcHVlamswTnpoU1FWQkRORlp6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT1ZGcG9XbFJDYlU1WFJYbE9SR04zV1ZSak1WbDZVbXhaZWtrd1RsUkJlRTVYVVhoWlYxWm9DbGxVVlRSTk1sa3lXVlJaTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTZFdKNGVtMEtRVUZCUlVGM1FrZE5SVkZEU1VKdlV6WXZWMGxEUjJKaE1WZDVlVFJ2TUZsemN6Vk5ja0p0YVhONlFYSXlNREpoZEdSNFUyOXNjbU5CYVVKRVVWaGpZd3BSWldwMmR6bDNPR1ZNYVZwT1JqZHRhVzQzYkdFM1NESkNhVll6TkdodFFrRktZWGs0VkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ2pCMFFreGFWblpzZUZBNVpsazBNVU5vVjBjNWJVbExaMWRxWTFoTFYwWjZaSFE0TldSSlJEVkZVVVJUUjNsc2NYRnpSMmwxUzBKdll6TnVORzVEYzFnS1FXcEZRVFV4ZFhabGIxWTJZbVl6TldkUE9GcExUMmx2YUZaTE1uZGlObGxxVDBWU1lYQXpNMGhIUlRCc2VDOXJlVmxOTm5GWGR6bFVhMkZOY3pncmJRcFJiRk01Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668300104,
          "logIndex": 6962166,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "756ae0f5a2470a75c4ec245015d1aeaa583f6a64",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3453183189",
      "sha": "756ae0f5a2470a75c4ec245015d1aeaa583f6a64"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

