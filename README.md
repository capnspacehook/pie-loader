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
| `latest` | `sha256:582cfa0b3b3a866fcde0a830a4711be5cabadf5e30c838cdb9b1431d37cbbbd0`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:582cfa0b3b3a866fcde0a830a4711be5cabadf5e30c838cdb9b1431d37cbbbd0) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:582cfa0b3b3a866fcde0a830a4711be5cabadf5e30c838cdb9b1431d37cbbbd0"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "fe58140271919ec49902abf8354b06058548a413",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCHc36b0u88cJXEFV37HhECAKdDz5i5qdz+aL7mqS+ECwIgOMp7DDEtUTkYn5zegTOOvS4cRcjqSrQ4mWaq8DX3Ve4=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3ZGE3MDgwNzFiYWNiNTUwODBiNmFhYzY1Y2VhNWQ3M2U2ZjU0MWJmY2JlMjM1YjlmNzg2NDAyNmQ4OWRmNDdlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNzWFZVTktFT2grYTljUVpOcTRlaE9aa1hFc1ZJb0FPV2UrSmF0azd5dHpnSWhBUDBZVjNJNUtZV2JJc1RiRHZrTTUxR1BvOGVsNWNMZnBTUUd0TFRzWjFTaCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVldqQjVVbFpSWlZoSmVIbHphRVpQUjJ0UlNXbG9WMlJLU3paemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVROTlJFRjZUMVJGZVZkb1kwNU5hazEzVFdwQk0wMUVRVEJQVkVWNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYwUVVzNWNtbHZRMGMyVG1oNGFtOVdNV0p0ZUc1UFJYa3dSbFZ5WTNOS1lWa3pORWNLYUd4WlYwdENTbFF6UVcxclNFd3labU5UVjFwbmNFZDZPRGxsY0hSbmJGcEhhRmQ0VkU1RWIyZEZXRmhpTkRSVlRUWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZsWkZCWUNtcFFLemhPVFhNeVNGcG1WVmhzYzFaMlVrVTRhbmRuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUcxYVZGVTBUVlJSZDAxcVkzaFBWRVUxV2xkTk1FOVVhM2ROYlVacFdtcG5lazVVVW1sTlJGbDNDazVVWnpGT1JHaG9Ua1JGZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaY0ZRdmMwb0tRVUZCUlVGM1FrZE5SVkZEU1VWSmJYTTFhR1Z4U1ZOTFJVTnhlakV6VTA5VE0ySlVZMGxxUTB0WGNqTmhSVTVKV1hWR1oybzNjblZCYVVKTWVEWkVLd281UWxOS1VIUkJUbFZOYVdabFRWbGhWME1yVlVKNWNteHliWEF5YjFsT1ZHOXhSbXhQYWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ25ZeVUwRllaemhSTTNGeFdERkhWRFZ6U1RjdmIxUXdkVXgzWnpoUU4ySktSMUJUYmtkT2JHSktXRlpIWmpSVE0wVkZaRk5DVlhCTVdYWjRjVlp5ZDFRS1FXcEZRVFpEZG1Vek1IbDFPRFYwSzNsR1EyRlZaMVZUTjNONEt6VjBTamxvVlZKYWJYWjJSRmgyZWxoR09WQllVMlJVUlV0eU1HMUhRVEUxTjFCRVpRcHNWRUp1Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675730377,
          "logIndex": 12780317,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "fe58140271919ec49902abf8354b06058548a413",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4109298020",
      "sha": "fe58140271919ec49902abf8354b06058548a413"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

