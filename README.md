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
| `latest` | `sha256:5c744443007076c23d68c1a65b7637ec1fd663714d7249c18b3b4f4825ab0180`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:5c744443007076c23d68c1a65b7637ec1fd663714d7249c18b3b4f4825ab0180) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:5c744443007076c23d68c1a65b7637ec1fd663714d7249c18b3b4f4825ab0180"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "db8dc0e68405a31803a987509affe9ba298820a6",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIEZrlIyy9/Q5A+6UoA1edJ1jScCdWysmQtVxYGMkVFx7AiBM8nWwhlQzG2tKrO5q+aM6VZYqazpmQroriVk2rEpD1Q==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzN2ExNjU5MDA1YTA0MTNjZDdhZTRjMzcyZWMwNWI2MjZjY2Y1MmYyYWY2YzRiZDc0OThjODhlODQwODllYmU1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJR0Z4UThrMjcvcEc5TDFMVVpKc3NrNkV2bXFLOFhNSGlabGVSeUN0eGt3REFpRUFpbm9oMEVUMGtlSENXNWM3RVlQbTBTSEl2czVvM21IS2lUZDB6Vld5cG5BPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCaFowRjNTVUpCWjBsVldURnhkbkoyTTFST09HSllVa05GVVhOM1VFb3pTM2xYUzBkVmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1hsTlJFRXdUVVJGZVZkb1kwNU5hazEzVFZSSmVVMUVRVEZOUkVWNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZQVjBKVGVXRkNiRUYyTDJFMVIyMVpNRE56VVRWTWRqSnpSbVpYYVRrNVJFNXlMM1lLWVVZd1dVdFpiR0ZXUnpkNFlUYzJNRU5CVkRWVFZqQmlTWFJ3Y1RScmJEVlZXVVZxT1hSVU1tdG9hMk15VlZwSWREWlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ5VlRkMENqaENUVXhSWkd0amNpOXFXRlY0YUc1c00ybE9SbTVOZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0WmFtaHJXWHBDYkU1cVp6Qk5SRlpvVFhwRk5FMUVUbWhQVkdjelRsUkJOVmxYV20xYVZHeHBDbGxVU1RWUFJHZDVUVWRGTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZVnpaNVdGWUtRVUZCUlVGM1FrbE5SVmxEU1ZGRFJDODNMMVowYTI1cmRWZE9TSFpwUmpsV1R6bFdNRmRHYmtOek9ESjFSVTFwSzFVeFlubEJPVUpyVVVsb1FVb3lPUXBJVTBJclIzVllZamRQVUVORFUybGtjMDVxVldkeVVWUXZNMk0zUVRSdVZscGtZVWhKYkdGS1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVkwRk5SMUZEQ2sxRVpuRktka1l2WTJOVmVTOVpVV1I0U0ZCTE1rSndSSHBOTTNWQ2JWaGhUMlpWUkd4V1p6azNTalZKTm5Jd2FTdFRiUzgyYUc1cFlUSnFObkZ0WWxvS09VRkpkMFJUYWpKeEsyVm1RMFI2YXpGaGRrazJVV1JESzAxUE1UTkZOME5OSzBkQ1NFMTRZM2h0VlhoWldWTnRNRzEyVEdKb09YQkRTbnBqZVdVeWJ3cElTbXB4Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674348032,
          "logIndex": 11677864,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "db8dc0e68405a31803a987509affe9ba298820a6",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3977309331",
      "sha": "db8dc0e68405a31803a987509affe9ba298820a6"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

