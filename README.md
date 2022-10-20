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
| `latest` | `sha256:8752bdd07513c2810a22caad45c0fc2d739e052d7ce39e73e8ff74339969a6b2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:8752bdd07513c2810a22caad45c0fc2d739e052d7ce39e73e8ff74339969a6b2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:8752bdd07513c2810a22caad45c0fc2d739e052d7ce39e73e8ff74339969a6b2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "ace10f8e9bcbb918176731a2d510c6d0c6a55065",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIE9YZN74eG+QUzoj/T+uujeBORVcQbGKTf/ubxpGpBJJAiEAt98TIedv6cW9O81VIKjImAop9byMknb3JTeC5JsN2Tw=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmMDE5YzQxMDVjYzdmOWFlOWEzNjUyMWMwZDM0ZjliOTE5NTI0YmM5MjI5MDU3NjY3ZTI4MDM1NTQwMzdjYmJhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNDMVZpdEV2MXVPeVJpc2oxQ210QXFxdDJpZnJoalJCQXd5SWE2KzBGYXFBSWhBTE5mQmtCejBOKzdON3ZVbG90ZVM5S2pxMVEyVDVlcmM4a1hjNjdDQk53RCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlkzVmpZbGROVGxGbFV6VnFSemRMWkhwVGVGRTJSbWRoVUcxamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1hkTlJFRXhUV3BSTUZkb1kwNU5ha2w0VFVSSmQwMUVSWGROYWxFd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZzYmt4V0wwVm5SM1V3UWpabWVWYzJURmN4YWpZdmExTXdNVTlSYjFkemJIVjJkRmtLUWxCeUwycHNlSGhqWlhwRFIwTlJNVmhLTjFsbGVERnZkME5XWWxKdFNISnpUVW80YldkelkxcENUMW9yZFRkV05FdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzWlhVMUNuTkdiRlZOVlRRelZEQlpOQ3RGV1N0RFVYSmFSMmM0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdoWk1sVjRUVWRaTkZwVWJHbFpNa3BwVDFSRk5FMVVZekpPZWsxNFdWUkthMDVVUlhkWmVscHJDazFIVFRKWlZGVXhUVVJaTVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxRZVRST1YwTUtRVUZCUlVGM1FraE5SVlZEU1ZGRGJEbDBhbHBYUzJOak5scG5lVGhNT0dsbVRWZHJSVTV5WmtsRlNHUlVabXMyUVVoT016Rm5jSEJyUVVsblZXVm5VUXBhUzI4dll6Vk1iRlpQTnpKQlREZzVWelZKTWpOUFFXSlNNVFpUYjNsRlUzZDBPWFJPYXpoM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGT1ptcDNZazFrY1ZobGJqQnhVVWRsYmxBMlMxZFRXVGRtUjJ0eVFqRm5LM1kzZUZSa0wyOHlRbTV4VFZRMGFuRTRlV3RKVURWMVVuaHRlRkppZUZnS2EwRkplRUZMTDA1R2JpODRObFJtWW5WM1ZXUm9URVpxU0c1WmNuUnNla0poZUVFck5VOVpibHB3UkVOcmRUaDROVmROYTBseFIwVm9lbGxvTVhJd2FncHNVR2RsWm1jOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1666227183,
          "logIndex": 5464924,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "ace10f8e9bcbb918176731a2d510c6d0c6a55065",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3286044060",
      "sha": "ace10f8e9bcbb918176731a2d510c6d0c6a55065"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

