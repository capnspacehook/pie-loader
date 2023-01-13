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
| `latest` | `sha256:1602ae349ed4bc896a968c2c6aa6abe48aa1851833bab82ee7fcd7c0b8dcef0a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1602ae349ed4bc896a968c2c6aa6abe48aa1851833bab82ee7fcd7c0b8dcef0a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:1602ae349ed4bc896a968c2c6aa6abe48aa1851833bab82ee7fcd7c0b8dcef0a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "e0336f0e6c7f34b9eec3da5ddf58214887534774",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCY5uRBeENfW/AcqZus5uTKHxGyBmsujSQNAhAKsEOJKgIhANjGwXO3x05mF2EHbaTKqKjas0C/z8Wg6q84T4mz7bDE",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI0ODhlZWJjMDAzN2VmZmU3ODNmZDY0OGFhZGEwNmY1YmNjMGI5ZmY0N2ZkYmJiZTRmOTgyMWI1N2I1OGE2Nzc2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNRcmNIcmVuaUhhT0FHRDkzRi96UlJQYjJzQ0pWa09VSlB4YU9PTmh6OXZnSWdWZ0tLRUdDL0t6TXJFOVNla0c1Qng4Wm93UkVJejAvVGVqb1k4WTFoQmh3PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJWRU5EUVRCVFowRjNTVUpCWjBsVlMxZ3JPU3QxV0VsT1ZuUkxPR1IzVkdoak5VY3hhMGhxWkZGemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUlhwTlJFRjZUMFJKTWxkb1kwNU5hazEzVFZSRmVrMUVRVEJQUkVreVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZXZURjM1ptRktaVEZIVVZCNllrZHNOVGxIYVVsdk5qZEZkVXRvZHpka1JIbElkbmtLSzNGeGNrOVhTRkpSYkZaUE9TdFhTM1o1TkZkM1dUVlhWa1p4YkZoaWVtdGhjblp4VjNkM1pUUktlUzh3Wm5JME4yRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZtZUZSM0NrRk1kVkJCU0hkblIwNU5MMnRJZWpoSFlsVXdOM1pSZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd4TlJFMTZUbTFaZDFwVVdtcE9NbGw2VGtkSk5WcFhWbXBOTWxKb1RsZFNhMXBxVlRSTmFrVXdDazlFWnpOT1ZFMHdUbnBqTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYYjJ0RmJGRUtRVUZCUlVGM1FrZE5SVkZEU1VkU2FrOU1lR3N6WmxOamQyb3lSbVkxZDFaSVVWWmlZMGhCTlZGRE1rbHZXUzlHVGtaYWVEWXZTVGhCYVVGQmNFTmFSUXBNZEVGSVJXSkRVMFJ1Vm5WS2VWUlplaTltYVZWeFUzQnVaazlxTVRCVk5TdFpRVk5CUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYmtGRVFtdEJha0pqQ2l0RlprdFFXRFJTVFUxek1YZFdTakZ0U25jMmQzWlRUbGRyWkVwYU5ETm5lSEZIWVV4RFpISlVSalZOWW5BNVF5dFNkRm8yTm5CcE5IQnBVVXRUVlVNS1RVTllOeTh5UXpNck5EWkZia0ZRUkhaUVQxSllTRWtyUjJ4NVEwcDVWazlFU0RKeVFuUldkMU5rZFZkYVRXbDNVMkVyTkVkNlJWaDZiR29yUVdKTk5BcEpVVDA5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673570334,
          "logIndex": 11057219,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "e0336f0e6c7f34b9eec3da5ddf58214887534774",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3907273830",
      "sha": "e0336f0e6c7f34b9eec3da5ddf58214887534774"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

