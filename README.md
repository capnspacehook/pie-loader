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
| `latest` | `sha256:4c6c73b4e3ae433cea91223b0ffcc23f267a392c18cfbdc6191d06174747e067`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4c6c73b4e3ae433cea91223b0ffcc23f267a392c18cfbdc6191d06174747e067) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:4c6c73b4e3ae433cea91223b0ffcc23f267a392c18cfbdc6191d06174747e067"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "8dde195e04629f442f0803aa508304a029de717d",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIDFHEwv4uSuponvDvlfUsPrPPiFcrtf303Z4wI0cCT8JAiEAlgVK2hdtvJygDvfuXwdTx2ypigaZizJh4UBdG6RqmXs=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI0NWNiNzA5MGRiYjE1YmZhNjU0MjUyZmMwMDFhNWFhMzA0YzllNjAwZDUyYTkxMzAwMWUxMWNjM2EzYzdlZTMyIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQ21BS0JVK2YxUUJ5TmE1TS90Z3VuS3h5OUxZTG1ZM1U2aUd3YkNzVzVwZEFpRUFuZ3YyWDdPOWNCTks5VG1aYmVmalRtcGFnS04raEdEd3lOeVFvV3FlZEcwPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlVsb3ZaalV2TlRZdmF6TnNTREV2ZWtScmEzcEtSSHBzUjJvNGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVVFhkTlJFRXdUVVJCZDFkb1kwNU5ha2w0VFZSTmQwMUVRVEZOUkVGM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZsYlU1WFYxUTJSVWRsZFRaM2EyOHJZbWcxTUN0S2NrWlpZakV4UW01M1lVRnJOalFLYkdkT05VZE5TRVZOVVRGaU1WTjNRMk13Y21OUFRtUmtkbTFJUTJ4aU0zRnhOblpwT0RBeFltMTFRMDU0UzNGSlEyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZJZG5kSkNsTmhTek5HTVUwd056VjVPVGcxVDBGV1QzSTNVemhKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpSYVIxSnNUVlJyTVZwVVFUQk9ha2sxV21wUk1FMXRXWGRQUkVGNldWZEZNVTFFWjNwTlJGSm9DazFFU1RWYVIxVXpUVlJrYTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVUml0bFpqY0tRVUZCUlVGM1FraE5SVlZEU1ZGRVJXWTNPRTFNTDBvNWNERTVVVWhMTkhadlpVRkljVlU1ZDFwMGNXTk9TbkpQV1RSQmIzY3hVVEJEWjBsblpXMXpXQW9yY1hGc2FtdG1jVFZKUmtabU1IcFZLMGg0V21zNE1IWm1iRUY2YVdoSGRuWkZUWEpNV1dOM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGUGNtVm9lVm96WTNOSFNFMTJhbTFtTUVzeVRHVkJWWFV6Tm01cWFVZzBMekpXV2s0MlYxZDVWVGRMYTJ4UVZFeHZZV3RFU0c4dk4wWnNaekZxVEUwS2JHZEpkMFJZU3pSWE9GTlNVbkJpY0hvdk0yNDFaVGd6U0ZOck16ZFljakI0TVdGTmFrTkxZM2N2ZDNWS1JHVkNPVEExTTNaQ2NHc3ZURkpXUkhOWWVncFJZbll4Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669768820,
          "logIndex": 8123773,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "8dde195e04629f442f0803aa508304a029de717d",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3579236672",
      "sha": "8dde195e04629f442f0803aa508304a029de717d"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

