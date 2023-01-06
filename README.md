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
| `latest` | `sha256:17bf718ef19946a7de4174e1a819c43607492be1848ae225d12ebdb18a90be6f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:17bf718ef19946a7de4174e1a819c43607492be1848ae225d12ebdb18a90be6f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:17bf718ef19946a7de4174e1a819c43607492be1848ae225d12ebdb18a90be6f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "d69103526bb5af34e7d6d955705894333434edd3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIAx4wsu9Z4HqRlsU6LS4UkyBLO5LRtXG93q2AzMmT5VTAiEA6cN45QhkYpN9nHAJPayAiO9l+HrXKk5oojHZhSyVnuo=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI5OTFmNzljMmY5ZTEyM2Y1ZGQzOTI5MjA4Y2M2MmJlYjhiOWI3ZjNjOGU0NTI4MTU4ZGFiZDM2MjQ5ZjBiZDg3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJSHdRS29FVFBkMDBsUGRYWE9qVHR0cEwraEovcnJIZXVVUlVxY3h0aFhNQ0FpRUE1WTY0emZKU0tnTzhKOFo3U2ZuNUxqZkM4am04Z2x6VFFNSW9pUXUyZ3BnPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlMxRkpaak5QVm5Oak1rWXpkVWszVUdadlJrODNWbFF4TVRaWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVRKTlJFRjZUMFJCTTFkb1kwNU5hazEzVFZSQk1rMUVRVEJQUkVFelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZzVlRONlREQlpOVU5CTkZGd0szUjFWVkpCZVRoeVZYTlJVa1pJUjNoSVJFUkdhbklLVVhseEsyaHRiSEk0UkVWdFkzQjZZbVZvUkc5WmRWazBWMkkwVVdWTE0xZDROWGxJVUcxaE1sWmpha0ZxTDFkMkwwdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZaUW5SSkNrMXdNemhTV1habVNXZFNVa3AyVGt0SlNYSTJhWEZyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0T2FtdDRUVVJOTVUxcVdtbFphbFpvV21wTk1GcFVaR3RPYlZFMVRsUlZNMDFFVlRSUFZGRjZDazE2VFRCTmVsSnNXa2RSZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYUldjemQxY0tRVUZCUlVGM1FraE5SVlZEU1VjMVZscFpPRUZEY1d0QlpURm1NMnBMVmpFNVlYa3lZVlJDV1RaUlNreEdlVnBXTkVwNVF6QldhVWhCYVVWQmRIQndNZ3BTUXpsbFIyWklaVUUzZFdScFJpOTFiUzk2ZFhncldrTjRVRkZZV0hCRFJYSTBVRk5SVlVGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGUFJrczVNMVUzVHpCcVVYRnVOamgyVUZnemRXZFVkWFIxVTNNdmVsbE9TRXhqVVhaeVozZzVOMWxPVEVFclRHbE1jVmxIZG14a1Fqa3lTMWQ2Wlc4S2IxRkpkME5uVkRVM04yUlFkalpDYzJKelFYaFJUM05GYkVjclIwMXBUblJzT0VGSVRsUmhTVmxoWkVONU1YQjJkRlZ2YVdoNFpUSlhTbGxQVm5JMFJRcDFhRlJGQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1672965519,
          "logIndex": 10563833,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "d69103526bb5af34e7d6d955705894333434edd3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3851543483",
      "sha": "d69103526bb5af34e7d6d955705894333434edd3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

