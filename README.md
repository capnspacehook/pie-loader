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
| `latest` | `sha256:ffafea5d5eddd8e2dacd3ebc26f5a8efbd67d3f44ed5250b64e8a0affb53ed84`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ffafea5d5eddd8e2dacd3ebc26f5a8efbd67d3f44ed5250b64e8a0affb53ed84) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:ffafea5d5eddd8e2dacd3ebc26f5a8efbd67d3f44ed5250b64e8a0affb53ed84"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "13341bf158d3ed5fc76948093038bb537aae1d28",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIAcwMrBTehKrKTKH3bzQ0kmWMedFNH7Zz3ESF2c4mJQ0AiAB3ibjG1rRa2w6KtGsslmjADTKve7jLXaKBKNGlqiW2A==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxNWRjYzYyOGMwMzE4MmI2MTU5MjZiOTE4ODY3NmY4NGE0ZDAxNjk4OWY0ODc5NmJiNjJmOGJkYWM0NzgwYjYwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRUFVeGRmYkZSR1o3Q25iME9YN25GYWFMNTFDR0wwak95MVJkcFVFN3lNU0FpQmlJRmJKTkhGTlBXZXY0K2puNGhQYTBMOEc4VkxQaFlDekFOM1V1ZEFJZFE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVllsTXhTR3h0T1hodWVEbDNTbHBoZGpOa1VqbElTRFJYZUdkRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlRCTlJFRjZUMVJKZUZkb1kwNU5hazEzVFdwRk1FMUVRVEJQVkVsNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZEWkRZcmNYUlBNVk0yU2tSSGJUQk5WMHRyTm0xb05HVmFSMWt2Yld0emFHTlZZVGdLU1VoV2RUbFBZek5pYVUxc05HWkdVbVEzT1ZObU4yeHNXR0ZwWmxONFZVcHlTVTlvWmtSakwxWlpVRFozT1RWcmJYRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZxSzJ4WkNuQklZbm8xZEhSalVVeEdOSEJTVEU5RGRrY3dVbXc0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoTmVrMHdUVmRLYlUxVVZUUmFSRTVzV2tSV2JWbDZZekpQVkZFMFRVUnJlazFFVFRSWmJVa3hDazE2WkdoWlYxVjRXa1JKTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhVGxoS04zTUtRVUZCUlVGM1FraE5SVlZEU1VoSE5EbHRUbVJGY0hSV05ubG5iRmt6V204MlpYUktVVlpWUzFJM2MzaHBUV015VTFaM1JYSjRlRzlCYVVWQksyWTNUd296YkdocFNuTTVZMHgwZGs1NldYSXJaMHhJTW5oUmJGVjVhazV2Y21ONkx6VXJOMlJXTWpoM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ2s5WFEwcFJjVEJrTldWVFRXaFNlV016Y2t0eU0zZDRjM2hKTDBweGRXbFhUMGRVWVdoQmJXMXNhMWQ1U1doc2QxZFJhblJZTmtONmFqZEZXVUZETTBnS1FXcEJOekJvUlN0Q04zRjNkRFEzUkRkMllXSjVMekpHV25CdmF6TXhjM2hoV2tGYVNHSkVSRWx5VkRGMU4xaFVWMFZ4U25VMEwydExMelJwUWpkTWJBcE1URGc5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676335190,
          "logIndex": 13285605,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "13341bf158d3ed5fc76948093038bb537aae1d28",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4169230540",
      "sha": "13341bf158d3ed5fc76948093038bb537aae1d28"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

