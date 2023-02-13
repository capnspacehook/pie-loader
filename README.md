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
| `latest` | `sha256:2b68728adde7ff52126a4f646d642f8ad497c3a19930f186d19e8c816d178dd8`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2b68728adde7ff52126a4f646d642f8ad497c3a19930f186d19e8c816d178dd8) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:2b68728adde7ff52126a4f646d642f8ad497c3a19930f186d19e8c816d178dd8"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4810f2ffb9ceb8a7b6a5310f60c7d8bc352dff46",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIBa5JD+nIDqeOldAltlpwGs6aj5NH8GlR/G0sxmS5M9nAiB84AQZWIPmkOnpAf14bfYOdgHdNUel8pHjRGRJ1CPDrQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhOTRkYTkzY2ViMTM2YTc1ZjE5NDZkOTYxNDkxZmE2Nzg5YzkyOWE5MmQ4NzY1YjNiNzQwYzBkOGMxY2JiOTI0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRWpxNkU5OURaT1paeWRtb2F3bWJyVU1EOFJTeUVzeUEreXBXUVcrWlBQeUFpRUE2RXIrSklqTEt4eVphdm11SVdGM3REdjdsZmhVVDJ5enVhQTFYRHN2bmIwPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlYwdGhSMG94UkdOaE0wcFVTMjE0Y1U1TGIxTTRTWHBtZFZkemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlhwTlJFRXdUVVJWTkZkb1kwNU5hazEzVFdwRmVrMUVRVEZOUkZVMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZQWVRKeVMxa3Zka2M1WjFoS0wxcFRPV3BvYURaYVoxa3hXRXRzU0hSblZqQjFlVTRLTUcxSlFXZEtTazlXY2tJNGFFMXBOalY1Wm1kTldpdFhTemhtWlRaNldUWklaM0pEUzNWRVZuQkJWR1l4YUhSeGN6WlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY2ZEdoSkNrSXlZazVoT0hsbldsWlhOVWt4UW1NM2NYZEdVR2haZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCUFJFVjNXbXBLYlZwdFNUVlpNbFpwVDBkRk0xbHFXbWhPVkUxNFRVZFpNazFIVFROYVJHaHBDbGw2VFRGTmJWSnRXbXBSTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhU1U0NFFrMEtRVUZCUlVGM1FraE5SVlZEU1ZGRFNUaElZbXBJUVU1dmNqSXlXa1pqUzNRMk5WZExTbGxpTVVsdlFtdE5OMkZ1UmxwM1pFUlRTamxQUVVsbldHYzVhZ3B5WVhkSGJVOVVNelF5UlhkTWNFUkdSR1IwYm5KTU4wbGtXRTVGTTFkSGVYSndRMVl6TUUxM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2twTlprRlJTMUY0ZGxkc2NrVkVVakZKWW14MU0weE5SVXR0VGtWdWNEVjJPVmRMT1ZaUVlVODBkamxxY0hoUUwwTk1UMVJsVjBwaVJuWldkWGgzTkVRS1FXcENjblE0V0hOT1VWQmtNRXAzZDNKd1ZVNUNVMFpHV0dWUlJsZ3dlV2czVXpsd0szQkRSa3RWTnl0RFRscEtXRTl1VVZaRGVIVk9NVU56WW1KRVdncHdiRUU5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676248878,
          "logIndex": 13206386,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "4810f2ffb9ceb8a7b6a5310f60c7d8bc352dff46",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4159034426",
      "sha": "4810f2ffb9ceb8a7b6a5310f60c7d8bc352dff46"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

