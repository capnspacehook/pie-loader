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
| `latest` | `sha256:94502a5ba84152611d6a5eb3ad1fe6ad820ee13942d4df87e6b0e2e886f69372`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:94502a5ba84152611d6a5eb3ad1fe6ad820ee13942d4df87e6b0e2e886f69372) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:94502a5ba84152611d6a5eb3ad1fe6ad820ee13942d4df87e6b0e2e886f69372"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "77b1298106a705691162c704b0cc31b6c522cd64",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIHFA0U1xTzqxZJLTcqUdJP/ThhCg7BL/dxS/OWF7WHNNAiEA4PMveJdLfq6IAFq6SswwvzRu+MME16LVm3BXToyNfYs=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhMDc3MGI5Zjg3Y2MyYzFiNzExNTJhYmE2OTY0ZDc4ZTRmMWIyNDQwYzhkOWFjOTc0NzkyODAxMTBmZWVmYmI1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNGYzdZUXJZYU5nWDVTbTgyc1VRaGZwdUgvc0ZsOEFNTEg4MWNEb3krMUpBSWdQMk11UjhNNVJ5cS9LYkN2bnE4Vkl1OWtoMm5JTlBYN0wwUjF5ZC81RzU0PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVllsUTRPRWgxWVhZcmJHaFdWekIxYzNkV2JIVmpUVzE1T1hNd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVhsTlJFRXhUV3BWTWxkb1kwNU5ha2w0VFZSQmVVMUVSWGROYWxVeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYyYVhVMlYxRXhSako2ZUZCSVJYQnZURUpHVGxRM1ZXbFRibVp1YkVsa1VrWlpTRmtLVlhGT1ZXcHRXblJVTkVoNk1rVnhlbkZyVW5kM1JTOVVhRTlYU0ZWdVUxbGxWRVU0Y2tkU1dqSnVOSGx5VnpKa1JUWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZqZGpkRkNteHhhU3RUYWxSUGIyWk9lRlZ2UjNwSlUyUnhRV1ZuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT01rbDRUV3ByTkUxVVFUSlpWR04zVGxSWk5VMVVSVEpOYlUwelRVUlNhVTFIVG1wTmVrWnBDazV0VFRGTmFrcHFXa1JaTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxSTVRBMk9Fb0tRVUZCUlVGM1FraE5SVlZEU1VSbFkzQjJURVkzTkV0UldFMVNWemRGUTFkU1ZHZ3JWMmhzU0ZKTVJWSTBOV1ZSV1c1ek1GTk9iSGRCYVVWQmJtVnZSZ3BZV1ZCUWNXTmFjbmxDT1hkQlVrTlJVazFqSzBWdk56STNURFJyVEZKTmVUVmxVR1ZETURoM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2t3cmNFTkRhak5tVkVSMmVrMUdabTh5VkVvMEsybHZLM281VVRVMGVrSjFRVGxyZUdkMlFWUkJlbVJ1YUVONmIwTXZVR296Y2pCVWVrRjVVRWswYzFvS1FXcENVbXhqWW1wMk5pdE1TRlkyU1ZwemR6WmllR2hHVTFkd2NDOUNXQ3MxT1dKV1pqVkZRbGcyVkRrd1pFVm5OamxHTVdkUVREWjBjbFpRYzFNNGRnb3pURlU5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667350400,
          "logIndex": 6323541,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "77b1298106a705691162c704b0cc31b6c522cd64",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3374027316",
      "sha": "77b1298106a705691162c704b0cc31b6c522cd64"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

