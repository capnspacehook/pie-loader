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
| `latest` | `sha256:f3a17937946783d80d2af030688c77c2ced1667f7ba657a2544cb1e0fdcbbaa1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f3a17937946783d80d2af030688c77c2ced1667f7ba657a2544cb1e0fdcbbaa1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:f3a17937946783d80d2af030688c77c2ced1667f7ba657a2544cb1e0fdcbbaa1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "5f5304ee670d46609bfbe206d81b31350801eb33",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCN6L1IehYDVNnNQfoMVRPCa+oe+BzCYbqFrlHJd/w6zQIhAN48bEEATwZH/iDlgVQWc1L47WTjGCQOh+ErA/+q2klM",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxODg0MjlkNzljZjE4OTE0NzNjNGVmODc4OWMyODkwYjZhNjFhYmY3ZDMxZWU5ZGQ2NzYzZGIyNWQ1ZGI0MzZkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRE9OY1diZC9LaDZhU2o2WHpXU1pDVXdJY1NDYTRXcDVwOWYyWjdQVkpiM0FpQlhRVHppVU1XMzFWeDQ5ZWRLMVk4WnVrRmlSS0sxaHpJbnlIUjZyWlpkMFE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlZYQTJRMlZpTVdrelluSXpZemxNYVZWVVRrRnFObUVyVkdaM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVRCTlJFRjZUbnBGTTFkb1kwNU5ha2w0VFdwQk1FMUVRVEJPZWtVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV5T1RkUlMxRTJOMUJtYlRCUGVrOWlaREJWYjNNNFZEaFFhVEI2YVZwalkyaEZiMWtLV0Zab0sxcE9XamxVUWtOSUsyVk9SVXRZZEZWMFRYaDBWMUJrVFV4TU1VaHFiVmRqWVV0aWQyZ3Zjbll5WTA5c1lXRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUzZHk4MkNtWkpXR3BWT1hoR1JrcFNaazFGYm1aRGVHWlhaMWhCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGYWFsVjZUVVJTYkZwVVdUTk5SMUV3VG1wWmQwOVhTbTFaYlZWNVRVUmFhMDlFUm1sTmVrVjZDazVVUVRSTlJFWnNXV3BOZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVWVd0T2R6QUtRVUZCUlVGM1FrZE5SVkZEU1VVdkt5OWpNazVzVEVwalJuRnpibTkwWmxOelNEWnBNbFpvU25Cek1VaHhUbVZuUTJkSmFXWnpiSGhCYVVGT1ZrVkVRZ3BuVFRWcU1IZFVXUzlIWmtwYWFEQTNUWEZDT1VWb2RFRkpWa2t3YWt4a09ETlhWRTl3YWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0V5Q2xwM1dYVllRM3BPVmxkNGJsWmljbWRLYm10SWNVSmlRMk5zVTFkRFRWaElWMlJyZEhsMGVtWTVXVzlKVFdoWU0xWnlhVk5GYW00NGNXcG9PRU53VVVNS1RVVklkbXBTV0hKWVRtWjZaMU5HUkdkNVVHcHVWR2x5TlRSelRUSk1hblpWTldSNldHeEhSVzVvTDBGb1FsZE1aa1ZsY0V4U1RIWkhkM2R6TVRsMlF3cFlaejA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670114268,
          "logIndex": 8386826,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "5f5304ee670d46609bfbe206d81b31350801eb33",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3610927009",
      "sha": "5f5304ee670d46609bfbe206d81b31350801eb33"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

