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
| `latest` | `sha256:d2250e037d058b5234a381f97fe596e8239bf60ea6c511ed38e8d34aaee3c445`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:d2250e037d058b5234a381f97fe596e8239bf60ea6c511ed38e8d34aaee3c445) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:d2250e037d058b5234a381f97fe596e8239bf60ea6c511ed38e8d34aaee3c445"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "086400034026f7f5b7b5735c67f3bd7ec269c56f",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCID0ZT/YuDN2mjuXbLmVGUfsEhBS78d3RJFkJ4JMI5q+3AiEA0YEOgReadwF3iFI/nx9wgnf0IKA6uNfHH7cnydguS2E=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlYjZlYjVmYjIyMjExN2ZkYWZmYjEwMGU2NzZjODYyZjQxMTdmNjM1NDg4ZjVlNzU1ZjJhNWQyMTc5ZWU0YTJjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNCTXVvcTRVcWNaUzd2WW9rckgrbXVyL09FSWluOUVlSUFkNUdsUkdrVFdBSWdCODdEWWxnZ21tMGpaV01ZQUgzOXlSQ2paQjh6Mk5QeUFBcEFDMUt3cEZBPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVldteENTaXR5ZUcwNWEweENTVzlyYjI5M2NFZERSbmhsZFc1dmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVRWTlJFRXdUa1JGZUZkb1kwNU5ha2w0VFZSQk5VMUVRVEZPUkVWNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZHU201b1VsWjJRa0ptUVZac0szZEhRekp4TTBKelp5dFZkbFZMUzA5blJrWlNWa0lLYjNkbU5sVmlPR3R4ZFhGc1dWQTVOV3RHYUdkUE1XdFpUVzFVSzFSbVFtcE1lRFExYUhKTk5YSmlhV014V1hWME0yRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZvVGtOU0NqbGxVVTkzVWtzeFFYTXdlR0ZvU1ZOcWFUUTRhVWMwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkUFJGa3dUVVJCZDAxNlVYZE5hbHB0VGpKWk1WbHFaR2xPVkdONlRsZE5NazR5V1hwWmJWRXpDbHBYVFhsT2FteHFUbFJhYlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTV2pKRVRsUUtRVUZCUlVGM1FraE5SVlZEU1VKWVRqRnFVVmxsZW0weVFuaExaVlZuY1RGbFpWTndUeTg1S3poeWNVSldNMjVFVW1JMFpYTnNabmRCYVVWQmJYWmFTZ292YzBOR1pVaGpkRzlxVkdOR0x5OTBUR1ZrYVdrdmFUaDBSbGh3VWpZM1pETjJNMnhRTUVGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTFdrSnVkV2QzWkdSNVppOTFZbTFPZGxGTFowaE9lR2hQVVZSeVpqQnFUM0V6TldoVE5IQk1SVlpVVW5VMFdGVnZOSEl3TkRoNE9GcDFVMGN5TmpZS0wxRkpkMDA0VjJwSVZURnJkMU5GZGtNeFRUbGxTVEl4ZERVeVVFNDRRVkl3V0hwWVpFbHRlRVpOUW5kUk9VSkZaakZ5VDFSUmVsTkhZVVI2U25oVFJRcDZlVXB5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667954679,
          "logIndex": 6755714,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "086400034026f7f5b7b5735c67f3bd7ec269c56f",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3424405595",
      "sha": "086400034026f7f5b7b5735c67f3bd7ec269c56f"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

