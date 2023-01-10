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
| `latest` | `sha256:4d5527b4ead63e565cca108d7ee0ef1c8d54681fde65569097ebe48847268266`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4d5527b4ead63e565cca108d7ee0ef1c8d54681fde65569097ebe48847268266) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:4d5527b4ead63e565cca108d7ee0ef1c8d54681fde65569097ebe48847268266"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "f7da7a61d8a74fd37fd250fb2a38588638a21434",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIC0rlbUrReMh8Ic32ghIYMgwcMtDtMLbqVtkhE5de3rjAiEA45+cAEMP/soNKPW+Ixp+MypZxB9PQKF2Y3QzZBHAMmI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwNmViOTkzNWU4ZjVmYmI5ODgzYjBkMzkxOTZhYzZjMGMwOGQ1ZTJlNmQ1YzgwZTJlNzYzZmYxZGY1NjJhZGE0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUM2MlY0TlIrYm80TGZ4ZW5ZWDdjT0QxRUxnZUc2MkttdkI2VysvQ2Z6SlN3SWhBTFM3d3dVbEM2enlYbTFVYkNjUmp4eDNocG1vbVdQNitLUkNvUFQreVhEKyIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlNuWTRhMFpLWjJaQ1ZXcEhRako0TTJKM2MxcE1iRnB5V1RoQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlhkTlJFRjZUMVJOTlZkb1kwNU5hazEzVFZSRmQwMUVRVEJQVkUwMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZwYVRKdmIwdGxkVnByWWpsUU5rdExhQ3MzTW5OYWF6WmpaMW80VW1sR2MyMUJTa3dLYm5SdmFWQkpiVkJWUkZWUU1FbFpibFJwVWxCS2RrWnplQ3RwUnpGbmFEVTJOVzFCUVVkcU9HSm1lbXB0U0Vwdk5uRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZzU3poTkNqSkVXSE5yV2t0cGFrcFdNSE5EYlRWSlduTjBNa0ZKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxT01sSm9UakpGTWsxWFVUUlpWR013V20xUmVrNHlXbXROYWxWM1dtMUplVmxVVFRST1ZHYzBDazVxVFRSWlZFbDRUa1JOTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYV2toc1JWb0tRVUZCUlVGM1FraE5SVlZEU1Vka1ZUTklXVmt2TUd3M1dGVmhRamhxWTIxVWVFNUdhbmhEUVdvM09HcHVWak5aUkc5TFFXcFdUa2hCYVVWQmEwaFNXZ28zYmtwcVpHMUljM2wzYTNseU1FZHZiRVpISzFObmFXZE5aak5ZVEZodGJEaEZURXRDWVZGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGS1RYSkRNMmxwV25oTVJVcDNPVWw1ZFhaM1dHeFdXbGd5Y0dZNVdTOVNNR1ZrSzI1U2RGQmhSbWxVVDBOd1V6aG5hVlV4TmxFdlNXRTFjRzExVFM4S1UwRkplRUZLT0VJMVFqbGxRMDE0TjBoNEt5c3lSRk5GUTFWV1psZFFkVGxIZFhOUWNXZFBiWFZpVUhGWk5GQkJSWGRPTkVFdlNFeGlNMjl1WlZsT1RRcHFhVGxUU1ZFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1673311212,
          "logIndex": 10834179,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "f7da7a61d8a74fd37fd250fb2a38588638a21434",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3879048103",
      "sha": "f7da7a61d8a74fd37fd250fb2a38588638a21434"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

