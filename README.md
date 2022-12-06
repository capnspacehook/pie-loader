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
| `latest` | `sha256:0d3776298b8e424b5cde08334542dd0d928ee890c844508f20fa01b5f2f34570`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:0d3776298b8e424b5cde08334542dd0d928ee890c844508f20fa01b5f2f34570) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:0d3776298b8e424b5cde08334542dd0d928ee890c844508f20fa01b5f2f34570"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "0fc49eab24cdafb2ea6e635f79af25c5fa4442a2",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDbqDl66xOOtIZs4SygoR4rLeGcP6MLhoYYX62CRuy93wIhAJq4mQoHfvxRixtZQZYhgc981s/Ey7CW6prBGhd9PwSs",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlZmUzYjhiNzNiYjY5OWQyNzQxOTkwYWNjMWIzNGFjZDhkMzNhZWQ1MTk1Yzk5NDU1MGQ4NWNhOGVlZmEyNjhlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUQxd3Mzc3F2aGFSeURxYmszRXRWZHlycElMT241TE00T2ZhWEc1cEt2K3BRSWhBTCt3ZE9ETlNWZDFmS1dpUW00dlRXZFZhWEViNWtBYWI3eVFGNzdlM2o2cCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlZVeFljM1F5YjNSUUwwRkhjM1ZNUzBJeU0ycFRlR3BIWjA1QmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVRKTlJFRjZUbXBOTWxkb1kwNU5ha2w0VFdwQk1rMUVRVEJPYWsweVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZOSzFwcVVteEZSalZ4ZFZGcGRTczVXblE0YVhreFNXSkhSV3RxZVU5MUt6WmlPRzBLVFc4NE1GSjNlR2xSVXpReE5VODBVa2hMUjFKaWNuRm5TRU00V0d4dE1uUmtjV3M0TjJ3eVIzWllka1ptTkZkd1NrdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY1T1hOYUNqbFFOMU5ZUW1oU1RHeG9hMDU2YzJGUlRsYzFWR2xWZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkYWJVMHdUMWRXYUZscVNUQlpNbEpvV20xSmVWcFhSVEphVkZsNlRsZFpNMDlYUm0xTmFsWnFDazVYV21oT1JGRXdUVzFGZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVYXpOUVREQUtRVUZCUlVGM1FrZE5SVkZEU1VJeWRteGhjVVZHWTI1bFNFRnZZekJRZDI1M1dsYzFSVU56WmpBd2JqTXpNalpvVkZOdE0zTjNhamhCYVVFdlZDOWtTZ29yTUc4MlR6UnVVVzVTWm05TlozZzNNSGd2TTJwUVFWTXlRV1prUnpCTE1FaDRiV042VkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0p5Q2s1MFFtcFJjVWRUUW1VclRqZDZVMnMwSzBkR2MwdGxWUzltVDBvNFIwVlFiR1YyY0hNd09YWlFkMUJYVlRKNlRrVllZVFZ4WVRoQmNXZERkRnBOTUVNS1RVTXJObk40VDBzNGVscG1Wbll5TmxkWVZUUTVXSE5aUnpGSVZWQnBkaTlyUVhWWk1WSllPUzh4V0hkSlZXZzNXbVZoZURaeWRsTlZZMmQwZUVWWGJBcDJRVDA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670287029,
          "logIndex": 8492524,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "0fc49eab24cdafb2ea6e635f79af25c5fa4442a2",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3625299905",
      "sha": "0fc49eab24cdafb2ea6e635f79af25c5fa4442a2"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

