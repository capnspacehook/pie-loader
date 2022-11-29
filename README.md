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
| `latest` | `sha256:73b375ec9d443e209a422a2108e7c09e1cafa307326e262a2deada4193b9a4ad`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:73b375ec9d443e209a422a2108e7c09e1cafa307326e262a2deada4193b9a4ad) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:73b375ec9d443e209a422a2108e7c09e1cafa307326e262a2deada4193b9a4ad"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "97cba63e38a7bceea4fb3e6581e5ebbcc3af4c38",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIDp8otR0FKMjBFTzKNt1BNuAJ1/JBEL2MAm4JMFKQIErAiBquTCKIzMUqB+ZEQ2pB7RDe3qlq7ebGWf3HboyY8hYWQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiYTRhZDA0NTIzZGZkOGM5YzRmMmQzMmE0NWMyMDMzOWU3MDA0ODdiMzgzZWIyMGFjNWI0NWZjMzYyYWFlNWM2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRDl4N3hhTlFERERINTIxSTRyb245S2F4TXpGMUcxa3NhejVVL0NleTRmekFpRUFpVDBxOUlybkRaWFh5WTcrei9UdW5yTjRvenZBTzBLR3VQZ2ZlZGxLOUZvPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCaFowRjNTVUpCWjBsVlZpdG1aMlJYYmxrdlRHRk1XbFZZU1RGQ2RGaGhSbEoyWlZCUmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RWTlJFRXdUVVJCZUZkb1kwNU5ha2w0VFZSSk5VMUVRVEZOUkVGNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV5U1U1YVQxWmFibXN5TDA1Qk1tSmhTalJ1Ym5JclVVZFNXVmRGYm5CT1pUZERiVlVLZWxOVFUyNXlTWEZrVmxSWlZFSm5NR05KTVhwcGVYTmlOVzh2U0hGbmRqQjFWRXBUVVU1aVpFcHdkVXRzYVVOTWRrdFBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYzTkdndkNubHNWbTFaZFdOVU5GcFdjRFJoVDJsbVNqUmtjazl2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWT01rNXBXVlJaZWxwVVRUUlpWR1JwV1RKV2JGbFVVbTFaYWs1c1RtcFZORTFYVlRGYVYwcHBDbGt5VFhwWlYxa3dXWHBOTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVUVRBMVFWZ0tRVUZCUlVGM1FrbE5SVmxEU1ZGRU9VeE9Za1ZoWVdwVE5XZHhRV3RLY0c1TFkzcDFNMkl6Y21oQmQyMHhXREIxTWpCbFJrRmlTV013UVVsb1FVcG9UUW93V0hsV2RWTjVTUzlSUXpsWVJ6WnNVWFpUVTFseVJrZEhiMVZrZFRadFdTOUhkalJWZEU0NVRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVkwRk5SMUZEQ2sxQk5saHdPR3RpUkdacVNYaHNSbHB2VTI1NVYwUjNjRmROV1c1UFMwcHVZbXRhTUhkQlkwcFVNbkpLYzBac2FtTTJUVXhQZGtaeFZHTnhiVmxKZHpFS01tZEpkMFpOVm5sbmJEUlFTRFpJVmxZclNuTTBVMnRxUldwSFRpOWtjV3Q1YmpSSlpWaHJaMmxuTms1VWRscDNSbHBYYkZReVlXaENabU5aZVV0TmF3cDNTelZNQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669682427,
          "logIndex": 8049923,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "97cba63e38a7bceea4fb3e6581e5ebbcc3af4c38",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3569904725",
      "sha": "97cba63e38a7bceea4fb3e6581e5ebbcc3af4c38"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

