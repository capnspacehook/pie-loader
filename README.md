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
| `latest` | `sha256:d82cf205795244256ad7e685f7f818b5854bfefd879c38a01627aa7ff97865cc`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:d82cf205795244256ad7e685f7f818b5854bfefd879c38a01627aa7ff97865cc) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:d82cf205795244256ad7e685f7f818b5854bfefd879c38a01627aa7ff97865cc"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "583ee86ff4c2d72a57252e1e5edfae4d8f6709ce",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCQcb1ALIo/rGr1QsrN3aMJrSGPvwqKeeXHKYfRWTh82gIgSNP7KpD4C73oqQUmEbt8YvQlQ5u2+j7ecjXHjuzm1qI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiYTgyOGVhMjliNGY3ODY5OWZiZTkwZDM4ZTgyOTc5OGFiYjNhNmM0YmE4YTZhODFjNzI1YmM3OGYwNmEzYzg4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUM2dUpUZTRKbUVpNkhaNExqSUwrMXpiRWtyQ0FqT3dkT0VvUHhyQ2RVSEN3SWhBTGFjTmd2QnU1VFRiQXh2VEh2Q0N4TENuWXNyeG5zbWxrMTRPbmFJSFk4RCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlNUQlVOM05wYVhKcFFqVkVlRUpDU1RnMWMyUjRkRWxUZFdnd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlRWTlJFRjZUWHBGTTFkb1kwNU5ha2w0VFdwRk5VMUVRVEJOZWtVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZzTjBWcE1sbHhlVk5TTUN0eFR6ZDJWbTB5TUZkaVRGTkdTVUZMUTNwWGN5dHhiVklLUzJrd09YVkRiekY1VDBKbFpGWk1iRzEzTWxOU1ZFZzJabUZrTUVseGVqSkhjVVEzVjNOalNXeFpOV3hsUjBFelREWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV2TUhKUkNtMDJiMk5xWjFOV1UweFJhakZ0WlhKWU9XUjRaRFpqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGUFJFNXNXbFJuTWxwdFdUQlpla3ByVG5wS2FFNVVZM2xPVkVwc1RWZFZNVnBYVW0xWlYxVXdDbHBFYUcxT2FtTjNUMWRPYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWYm5wS1dGZ0tRVUZCUlVGM1FrZE5SVkZEU1VFeFkycFBXVTVWZW5kWWRVSjBSRkIwYVROblUxVjZOMjF0YW0xNlZsZFNORUZ5TW1NdmNUWk1VekJCYVVKaFJqRkdVUXBMTjBnd0wzRTBNSEozUWk5TE9GQlVkekEwWlhJM2VtZFRTMFV4UVVaalEwNWlWemRFUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0p4Q20xWFIwVlRaWGhKYXpkelVWazJiVlpWWnpKUGVFaG5ibGd6UTAxSU1VbEtRamR3UVd3eVdFUnRSSGhhVWtsMVJsZDFRMHRuTUd0Uk9FODVkMk0yU1VNS1RVSTJVVVpvUjAwdmRqWjFkRTkxWnpoRU4yNVhVV2d3WmtweVlsSnFWRGt3V0U1NFltOW9aRlZJU1ROWGJ6WmhRazFLTDNwNlVsRm5iRGczWkdKVlZBcEZRVDA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1671410019,
          "logIndex": 9373326,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "583ee86ff4c2d72a57252e1e5edfae4d8f6709ce",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3727327570",
      "sha": "583ee86ff4c2d72a57252e1e5edfae4d8f6709ce"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

