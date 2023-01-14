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
| `latest` | `sha256:4a625c01566a95992a835d6aaaec939101ccfd0b90f1ce77f5fcd733229a8c31`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4a625c01566a95992a835d6aaaec939101ccfd0b90f1ce77f5fcd733229a8c31) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:4a625c01566a95992a835d6aaaec939101ccfd0b90f1ce77f5fcd733229a8c31"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "6fb385c77bcb3e107b0040cf05805986c03b8b48",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIA6YjNTikzUqn0vzRQzwMCxbmtMXUNun6hICO8czYfh+AiEAqrEx4v+GXhyo5B4dMSmRaQin7sZmip2gGbMCY171FPc=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlMzZlYzE0ZmYwNmQ2MTk0YTI2MTE3OGJiZDVhNzg1NmMwMzIzYzQ2ZTFiM2ZjNmQyMjAzNzA5ZjFkZjAxYWViIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNDMzkvdXZPZlRHeEpnckpnUmVVVnFsdUh3TVNkMkVvZDliUEFCTitVVEp3SWdDV0FWUnoyU0RXQk9lQ2lTMWd6aFlWQSt4eW1tVFZpSUFUZGdjaUJuTGpvPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlQxRlFaSEJpUjNObVpVNVhUSGhRYmtKRGR6RjBUVXhNUkdGbmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlRCTlJFRjZUbXBCZWxkb1kwNU5hazEzVFZSRk1FMUVRVEJPYWtGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV6YkRWQ0swZDVkMWRIU25OUWRtaElWVlV6Vm1SdE1GSkRkWFZVZUZsMEwwUm9jRElLZGxsRVJGSjJhRlZrT0ZkWmNHMUZlbEF4ZWpWQ056QlBiMFZGTjFSelZHZ3dOa1JNU2pVcmJuTkthMmhRVW1oVFluRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZUWTJkbkNtOXJjRXRsVFd4b2NsUm1SMkpJYW1aU2QwbHljV3hqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpKYWJVbDZUMFJXYWs1NlpHbFpNa2w2V2xSRmQwNHlTWGROUkZGM1dUSlpkMDVVWjNkT1ZHczBDazV0VFhkTk1razBXV3BSTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYZEhSSVlUVUtRVUZCUlVGM1FrZE5SVkZEU1VadUwzRmFaamRpZEVoYVpVaEtOVUZ2WVd0c1JUSm1OMU0xUjI1dlNtSm9UbmxYT1ZwM2FtbENiWHBCYVVGU2RuTm1UUW95WlhCRVIzSkVVV2N2VjFsRWNIZHBjeXROTlhBNVIxVlhLMHhvUTBGRlIyRk1jRGhpVkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha1ZCQ214R2IxWlVZU3RqTDI5TE1VUnZNVlI1T1ZoclVtUldOM3BtWlU0dk5HUkVSWFJaTm5adFQzbFRSMjVHYmtGME5GbFhRUzlaY0hGdFNtSlVPR2x2THpJS1FXcEJSazlGY201SGFHbGtXa1ZXTkM5YVVtTTNjemx3Y0hKVVlsbG9SVzh4ZUUxV2MxSTVRWHBEVjNGTFIweEJialZUZEZreGFUaEJWSEl4YkZaeVl3cE1XWE05Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673656582,
          "logIndex": 11128205,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "6fb385c77bcb3e107b0040cf05805986c03b8b48",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3916006228",
      "sha": "6fb385c77bcb3e107b0040cf05805986c03b8b48"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

