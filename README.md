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
| `latest` | `sha256:b4cc4257ce57aaa021f7f6dc4fd38783f591d433eb50a89a024c84cb4af28955`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:b4cc4257ce57aaa021f7f6dc4fd38783f591d433eb50a89a024c84cb4af28955) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:b4cc4257ce57aaa021f7f6dc4fd38783f591d433eb50a89a024c84cb4af28955"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "be77b07f61d3612dccc32508c20e8fcca4a79e01",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFn85DBlEnprCNTSiuqO7NTmgY85Vrwlc85azi6fUHTgAiEAgei/h4U8ZnWccpBSz1SF6iSUFY9yHVmWZxIvVx95shY=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxNzA4MzIxYzdlOTQxODI3N2YyNTI4YjMxZjJlOTg1NGQ2NDNjYTJiNTY5MDkzMmUyYjM3MDQ1OTYyNGVlZjZiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQ0JYdC9SOE1RZUVMVVRPcGN3anNQbkRnQ3h6TldFQk5Ec0xQVUQvRGo4TkFpRUF4cXRnK01jd3RqZWZreExoUGJLamZyekpHK0VEMVR2cTh5aFNGL0xvMWVVPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlFURlZSRGd5VGpaTWJHOUlkWFlyWjNoQ1JGRllNMEZzU1c5bmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1hsTlJFVjNUVVJCZDFkb1kwNU5ha2w0VFVSSmVVMUVSWGhOUkVGM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ3YzBoclExbGlNQzl3UmtKWFZXTXphMUJwUlVkWE9HbHBZeXRWVXpaS1oweG1kMlFLU0VadmQyOHlLM0Z6WW5kWWRuWm9VMXBwWW0xYVEyRlhOR2x0V1c4MVp6VjBaM0pVVlVwWU5XMTZNblJ0YmxWeVYwdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY2VmxOQkNsazFXVXRuVEhFNFRXSlFVMnhtV1hwdE1IaE5UalZGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdsYVZHTXpXV3BCTTFwcVdYaGFSRTB5VFZSS2Exa3lUbXBOZWtreFRVUm9hazFxUW14UFIxcHFDbGt5UlRCWlZHTTFXbFJCZUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxRT1U1RVZsSUtRVUZCUlVGM1FrZE5SVkZEU1VoaFZIUmhabEUxVW05NVFVWjVVbU5IZWs1VlZUTm5aWEI0WW1ObVVHc3lSelk1UlROMlRFeHhVRGRCYVVKV2N6VXdTQW80UzFOalkyUnRVa012ZUc5a1Uza3pkVE5OYWxsdmNrSlRWMGROTUVSUWJUVXJMM1JwZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ2pKUVlrODNLM1JhTVVkd1JXTk1jekIzVXpKNmIySnJTbWRhV1RsaWIwVm1jRzl3VURSdWNubHdhSGxSZUV0VE5USnJPSGd6WkhkcWNWWnZXamx3YmtrS1FXcEZRV2hQY1V0c1JFUnNLMWhQVjJ0M1V6UmtkRkpoVW5kMk5sRkVLMUJFVURNd2NYZHFTMnBXVDI5V1kzbE5OR1ZsT0dGR1NpdHpSMVF3Y25oeWFBcENPRlJFQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1666400432,
          "logIndex": 5608292,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "be77b07f61d3612dccc32508c20e8fcca4a79e01",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3301361490",
      "sha": "be77b07f61d3612dccc32508c20e8fcca4a79e01"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

