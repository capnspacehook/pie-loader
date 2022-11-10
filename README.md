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
| `latest` | `sha256:88b9033f33410b97e18b1a470b089b2c31fa04ae9a270756e9d351bad0c16c2e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:88b9033f33410b97e18b1a470b089b2c31fa04ae9a270756e9d351bad0c16c2e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:88b9033f33410b97e18b1a470b089b2c31fa04ae9a270756e9d351bad0c16c2e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "a0cd33c6af31724748f749e64c0e1d70242c2180",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQD+aQl/aWgxe5OUMWK7Rtaij3GRA3N7Kiz0Wk6a3QxdiQIhALK5IBVv8tvqsX8S6PYp2+XTf0EjgpZaV9Ona2pON0Ke",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxNDhjZGRkNDQ5MjI0Y2U2NzY3NTliYmE1ODE3NDFkYTQyOTBkZDg3ZTRhYWU4MTE4OTg5ODAyMzMzMmU2Y2FmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUM5aXFmelVLMklKcHB3SkZvN29UNkJUbVBCNkJ4dThxZUd0VVlsVktQSnFBSWdMYzFHUGxzVjlUbHRjZk14S2lBbU9LSEhQMnhQdU1UVEtQUVNEdDVmM2hzPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlYzUkNjVUZHZG1Wc1YwcHFhMEpLU0VZd1JtSXdOV1Y2U0hsdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlhkTlJFRXdUa1JKTWxkb1kwNU5ha2w0VFZSRmQwMUVRVEZPUkVreVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV2VjFOTFNYSjFlVFppU2xSdVFYQmFTVWxhT0RsR0sySjJWUzlhVlZRdlFqbHRhRVlLUlZSWmNFaHpaa2xxYWtSQlR5OVZTMEZyZDFCeE9XMHJRV0pFUVhaQllqSldhblpYY1VWYVFqYzNLMDVqYkhGMFkyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZLUjJvNUNtVllPVE5QYzNkamRVWjZOREJJUnpSUVVqVjFaVWc0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdoTlIwNXJUWHBPYWs1dFJtMU5la1V6VFdwUk0wNUVhRzFPZWxFMVdsUlpNRmw2UW14TlYxRXpDazFFU1RCTmJVMTVUVlJuZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTWlM5elkxSUtRVUZCUlVGM1FraE5SVlZEU1ZGRE0wTXZaRkpyZWprdk5uWkNTVmg1V1RGNFRGRnpjR1p5VjFWd1MxbG5iblZsYVhOb09ESTRaVUl3VVVsblRrUTFUUXAzWjNGS1lXMXNWVlV2WTBOVGIyUnVkMjFMUXprcmVHeFJWSGgyWm1FeGJrdFJaVEZYUkZsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGS1psSk5WMUJ2YkRaeVkxWm1SbFUyV0dreWFta3dNMk0yVUN0bFpHeEdlR3hDWWxnM2NUZGhla2s0Tkdsa2RqVlNjbkZ2YTNKS1Nsa3lWM1ZMWmtZS1EwRkplRUZQUVdKVGFtRnpORTg1Tm1FclNVeFBkbnBqY3pSSFZWSlJVbmd2YW5Oc1NVbHZSVzg1VWxkV1psbDZSWE5RVUU5RVlsaGhSWFpoVVd4bE1RcENhVVJNZVdjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1668041088,
          "logIndex": 6804529,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "a0cd33c6af31724748f749e64c0e1d70242c2180",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3433033895",
      "sha": "a0cd33c6af31724748f749e64c0e1d70242c2180"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

