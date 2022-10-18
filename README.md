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
| `latest` | `sha256:c562c1b1bf146502e060ba837f6ab7fa946f66f8cc1cdb712b69d0f424c905ac`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c562c1b1bf146502e060ba837f6ab7fa946f66f8cc1cdb712b69d0f424c905ac) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:c562c1b1bf146502e060ba837f6ab7fa946f66f8cc1cdb712b69d0f424c905ac"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "workflow_dispatch",
      "1.3.6.1.4.1.57264.1.3": "5fd2230405af88ca246b6700695f037de9cfda1f",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCGivfING7Y5wuRZ4Dz2bSSyXrQfdwELtGS0aGrBZ7usAIhAKkA3A/qfMjsbugefQeHsACz8JjYPQR95XsQeWrJwdxJ",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlNjA5NWJjMTI5YThlMDQyODIxMjhmYzkzYmZkZmY5ODRmOWY2OTU3NGYzOWQ2NDZiZWQxNTU4ZWU4YTRkODJkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNhcytpUFdWbnpOL09UYUZneHcvNDVTalJ1bHdUT3BwRDU4a2o2ZHNPc213SWhBTWIyeXhjT05hZ3ZDemZicTJsYWxtRG9ZZ2NZNVhZYkpLdlNQbGF5cjhLNiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjVWRU5EUVRBclowRjNTVUpCWjBsVlNGaEhkVFJ4YUdsTVlrTnNSMFJzWlhBMVFURnFiRUZUV0dGemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRSTlZFMTZUbnBSZUZkb1kwNU5ha2w0VFVSRk5FMVVUVEJPZWxGNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZrWldGUFlURkxhM1ZxZVVKVmFtcEdZV3AxVW5aVmNUVTBPVlpMTDJoNlF6VlNla2dLZFM5RU9HdE1hWGhCTVhocmNGVnJOMUZoT1ZOQ2VpdEZkMnRhYzFFcldsZDFNRmc0Ym1seVZsSjNiR0o1ZHpJMllXRlBRMEZ0TkhkblowcHhUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlU1YzBOMkNsRnFXaXRzYlc5blJEQTVhMU5OU1dGelUxWmxibVJuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGbVFtZHZja0puUlVWQldVOHZUVUZGUTBKQ1JqTmlNMHB5V20xNGRncGtNVGxyWVZoT2QxbFlVbXBoUkVFeVFtZHZja0puUlVWQldVOHZUVUZGUkVKRFp6RmFiVkY1VFdwTmQwNUVRVEZaVjFrMFQwZE9hRTFxVVRKWmFsa3pDazFFUVRKUFZGWnRUVVJOTTFwSFZUVlpNbHByV1ZSR2JVMURkMGREYVhOSFFWRlJRbWMzT0hkQlVWRkZTR2sxYm1GWVVtOWtWMGwyWkRJNWVXRXlXbk1LWWpOa2Vrd3pTbXhpUjFab1l6SlZkV1ZYUm5SaVJFRnRRbWR2Y2tKblJVVkJXVTh2VFVGRlJrSkNhR3BaV0VKMVl6TkNhRmt5Vm05aU1qbHlURE5DY0FwYVV6RnpZakpHYTFwWVNYZElkMWxMUzNkWlFrSkJSMFIyZWtGQ1FtZFJVbU50Vm0xamVUbHZXbGRHYTJONU9YUlpXRTR3V2xoSmQyZFpjMGREYVhOSENrRlJVVUl4Ym10RFFrRkpSV1pSVWpkQlNHdEJaSGRCU1ZsS1RIZExSa3d2WVVWWVVqQlhjMjVvU25oR1duaHBjMFpxTTBSUFRrcDBOWEozYVVKcVduWUtZMmRCUVVGWlVISlZTRWg2UVVGQlJVRjNRa2xOUlZsRFNWRkVSM1p2VmxKd1YwczRVRXhEY1U0M09YUTRZMVpKVG5weFNYQkJTRTFWVUV4aGFVdGtNZ3BXYUZaNVJXZEphRUZQVG5NcloxUnNNbEZLY0VKaVFuUmpTMGxvU2xseFNFYzFRM2wzTmtkYVJXZFVjVkZCTVdFeVltZzBUVUZ2UjBORGNVZFRUVFE1Q2tKQlRVUkJNbWRCVFVkVlEwMVJRemhsYVZOVlpuTnBjMFpaVUZCUU5pOXpaR3RLYkdnMmFFNTBiR1V6TkdrM2IyTXpZMFp4TUU1MFoyRjFNR0ZOZUZrS04yUnNMMHhxYW5SdldFOUZUbWRCUTAxRVF5dFZSV05oWkRCV2MxcEtUM1kxYUV0U2JEZ3pOalpyU3pacFNFTlhWM0ZKY1ZWWVdqaFpaM1JtTXpCc2JRcFpiWE5uYTJ0elMwOXdTRVZwWXpVMksxRTlQUW90TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1666100282,
          "logIndex": 5355381,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "5fd2230405af88ca246b6700695f037de9cfda1f",
      "githubWorkflowTrigger": "workflow_dispatch",
      "run_attempt": "1",
      "run_id": "3273908249",
      "sha": "5fd2230405af88ca246b6700695f037de9cfda1f"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

