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
| `latest` | `sha256:d773a4d3ef1055a4bd02f452baa000149bab9abd228b8601fb19794474e42ab0`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:d773a4d3ef1055a4bd02f452baa000149bab9abd228b8601fb19794474e42ab0) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:d773a4d3ef1055a4bd02f452baa000149bab9abd228b8601fb19794474e42ab0"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "747531c0caa688c7807c73801ddbcff3442de3fb",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCICf6G+XSjFAZmixRQb0LcPf18b9GWIofUYG2HRMjajH6AiANUZOPGYlyanWyDyefG6oeufDZb6tNDApx2IOAxnApKA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlY2Y4MTU1ZjlkYTRjYjdkNTI3MGJiMjVjM2QwOGFiMzU4NzJiZjg2ODc3NGQwNWJhYjBlZDAxYWEzOTk0ZDJkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUR6bnZBWSsrVHE5VGQ5SGFEdWt5NlovZ1kzSVdrZEM3ZmxiNjZNY1RmNXR3SWhBTTlpT3BWOFRscWYzRzdpcSt1Y2lPcFM0cnRlRVpldVhBQ3gwZ3lzeFZTWiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlQwMTBNWGRDVFZKUWJVWXlaSGhxSzBGVmJ6Uk1jV1EwUVhKdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVhsTlJFRjZUbnBOTlZkb1kwNU5ha2w0VFdwQmVVMUVRVEJPZWswMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ4V0RKWmFYRTVkRGhUWkZKRFkzSlVZMU5UWjJoWmVVdDNORWRzZDBSa1NYZ3dTVllLUjFNMFlXTnpNMXBtVnpsTU5VNVZTV2hzUjFONWNXMHpTR3hSZVRGcmVETnpiMFl6Tm1WNmNHRk9UWGRyUzFoRWRHRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZoVVcxQ0NsWnRhWE5hVVhsNVVFeFdlV2hRWnk5dWQyeDNjbVYzZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT1JHTXhUWHBHYWsxSFRtaFpWRmswVDBkTk0wOUVRVE5aZW1ONlQwUkJlRnBIVW1sWk1scHRDazE2VVRCTmJWSnNUVEphYVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVVVZKSWRIRUtRVUZCUlVGM1FrZE5SVkZEU1VSTFJqSkpLMUJhUzNaNGExaHRXRW8zVmpWd1UxVjZSbW95ZFUxaWIxbGFPRUpvTTNreWNUQTJhbmxCYVVKV1FuSTBSd3B3VW1OWU9ERnpiWFZ1WWxKNVVEaFhjREkwTVZkaFZ6ZHpTMkp0TVVOMlNIQjFTaXRqUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ2poaEswNWpOMGxoYm14TlVtZ3lZVWsxVWlzelowTnBObUZvTlZad04zTlZlVzVsUVdoaE0zRnJWa3hpTVhJd05YVTBObE4wYzJwdGNtdGllRGs1VFhZS1FXcEZRUzlqVEhSc1pETTVjV2htU1RCcFNVSTFOazltZFZoNmJtNW9iRGsyWlhwaVVqQjZXR1JaU0RaSWVrVnJVbGdyUTBkRFV5dDFiVmtyZURsaFdBcFphVWh6Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669941492,
          "logIndex": 8259995,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "747531c0caa688c7807c73801ddbcff3442de3fb",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3597795280",
      "sha": "747531c0caa688c7807c73801ddbcff3442de3fb"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

