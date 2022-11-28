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
| `latest` | `sha256:e376dd5898ecf297386228a20f7f886839f56a23e29a7ce478babf1167bed595`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:e376dd5898ecf297386228a20f7f886839f56a23e29a7ce478babf1167bed595) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:e376dd5898ecf297386228a20f7f886839f56a23e29a7ce478babf1167bed595"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "c1667678b1673952ec45bdca2ae06e2fc7f96e12",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCXdM1P+U24g0aA8ibvXDiFaw7Vts7+sR1vqReAqKXuaAIhAM/TUREvk5P8VmKu1Otr8ipHl5AcSwgI1hRbXNMl7OHa",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwYjUyNzI0YTI5Nzc0N2I2ODM5OThhYjJmMWUxMjMwMzExNjA3OTQ1NjJmZDc1ZjQzYmRjYzJlNzg3MTA3OWNkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNwU05BNWdjcHEzcVRubGU1RVE3R2Q5U3FMblBiajhtdGJyc2gycThTNkhnSWdMcnlJbUt4TXI1WExjbXQ3US8rc1ViaXVnWmhjQnJuMm1Xc2UwUkVVb2F3PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlMwNXpTRVkyVTNwcFVURmtOREZTWkVWM1dFcElUemN6ZUVoVmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RSTlJFRjZUbXBOTTFkb1kwNU5ha2w0VFZSSk5FMUVRVEJPYWswelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV6VFZCTWVFUmpNbWx5UlZCbVZXcEhkVVF3Vm14YWJYSTNjVTFSTm5CaE5FbEhWbmdLWkVKM2Vta3ZXVmx0THpGQmFqbHJjVzVJUTBjME5tUndXbHBHZDIxdmJHOHpkMEpXVEhwdFpteDFZM1pxU2poalprdFBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ1YVcxU0NuVm9WV0pqV0VvdldGTnFOM1ZpWkVSbmNXMVpZMHh6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwTlZGa3lUbnBaTTA5SFNYaE9hbU42VDFSVmVWcFhUVEJPVjBwcldUSkZlVmxYVlhkT2JWVjVDbHB0VFROYWFtc3lXbFJGZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUTjNGb1pYUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRGEyVjBZbE5yWWxaTFkybElibFV5ZEdWWmQyVjJTMkZEVW01b1EyMW9ZbTh2U1ZZM2NsZFpaVFZXUVVsb1FVeFdjQW95YUVadWNrSmhOM2s0ZFVRMk4zbHRjbkE1TDI4NU5VSm5lRXBQZEZkTlUyd3lVV2RuWWt0a1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxSVpsRkRWbkF3VG5Ob1JEVXdhbEJNV2xSSVVtWlJiMlZHUTNCYU9IWnNVMnRSTDJSUlUwcFhNVGw1TldabVJYVm1TRk5QZEhoaVVHaFhXWEJuT1drS04yZEplRUZQZVM4dmNHUnFWbFY2YzBkMmNHTXZRakZsUlZvdlNIZEhhMFpwZW10QlZEQkJRbVJEWVhock1HVkJPRlJTVWtWdWFrZFJhMVJJY0RkUWRnbzNkVkYzZDNjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1669595816,
          "logIndex": 7978825,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "c1667678b1673952ec45bdca2ae06e2fc7f96e12",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3560707624",
      "sha": "c1667678b1673952ec45bdca2ae06e2fc7f96e12"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

