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
| `latest` | `sha256:cccee9945021d3c0a09ed1ef2c698d597b83cb74d60b9bbd62fa2a47603fa486`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:cccee9945021d3c0a09ed1ef2c698d597b83cb74d60b9bbd62fa2a47603fa486) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:cccee9945021d3c0a09ed1ef2c698d597b83cb74d60b9bbd62fa2a47603fa486"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "741ed50b6b52393596da6dd02d35d4a9e167f98a",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIFzbZ5GgXp0uf7uB0BuZGRtekY8HeP2YXqCy5PC05v7uAiAIxc0CRAKAhvVoOI4bq2aFXXzgrN7KG5O6fmmj5rBauA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiMDc3MjU3YTFiN2I1ZWE5MDQwZmI4YzgwYWRmZmYxOWE0Y2E2NWU0NTUwYmVkOTkyOTQyMDJjMTU3YjRjMGVjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRHV5eTRPdHRYQThDOFAvMHlIdXFvRGZyK1hUQ1YrT1hWeEE1VUhLYmtjUkFpRUEzWlhqM2FSSmk5c1AycE55MnJ0NU9tbC8xNlF3MFJoM2dZQTE2RjZnRVI0PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlIxRkVhMmRrTVZkT0t6ZE5lVnB4TkU5TlYwNHlLemc1WjNkemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1hkTlJFRXdUbFJCZVZkb1kwNU5ha2w0VFZSSmQwMUVRVEZPVkVGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZJWlM5MWJGRmtMMkpTUkU4NVJXZFBXbE5zY2xWMU5XZFROMnd2TVRWNVVHdG9XRThLZVdsS2RuSlRRMkpCYVVoRVVXVnFja0pRTHpKTGRpOWxhRkJLTTFkQlYxUjRNelkwTDI4eFRHODFRVVJMTURScVZUWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ4TUVsUkNsVlhZME01UnpsWU56UmlibUU1UVcxM01UVlVWMDVqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT1JFWnNXa1JWZDFscVdtbE9WRWw2VDFSTk1VOVVXbXRaVkZwcldrUkJlVnBFVFRGYVJGSm9DazlYVlhoT2FtUnRUMVJvYUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUVTJaMWVGa0tRVUZCUlVGM1FraE5SVlZEU1VRNVYxUnFaazFFVTNCNU1Xa3ZieXRNYVVSRlJqTjROalp1YVZBeVlUQmhVVlpRVUd4bWJsUlhWVmRCYVVWQk9XOVBOQXBNVW1oSVpVUTVZemxGUWxNd0wwMTBSM2xuTjJaUGF6VkhOVlZqYWxoTVlqRkxURkJMWlZWM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2t0TVQzQmhPR05EVkdwM09URmtVVXN4UWtzM00wbFhOQzgzYkhORlVHOTNiU3RIVUVwTFJFVXhRVWhaTVRKWU5tWndiVVI0YVd0cGQwRlFPREp5WVRjS1FXcEZRVFJJVERoVWRUWlRlRXhEWmpKWVVtaDBZM2MzWXk5SGRVd3JNbWRCVnpsVk5IbHRkWEpaY21ReFZuRm9ia2xFUkhjMFVHeGFSRVJWUm1aaWFncG1ibE14Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1668905120,
          "logIndex": 7447792,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "741ed50b6b52393596da6dd02d35d4a9e167f98a",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3505821932",
      "sha": "741ed50b6b52393596da6dd02d35d4a9e167f98a"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

