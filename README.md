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
| `latest` | `sha256:428c969a71cafc325c15d550affce2cb04d90a7e8af5ce74c848e334171c2c1d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:428c969a71cafc325c15d550affce2cb04d90a7e8af5ce74c848e334171c2c1d) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:428c969a71cafc325c15d550affce2cb04d90a7e8af5ce74c848e334171c2c1d"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "5d00259ce6954fe43d233ced6ee4c8dae6b9b07e",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQCY+T86J2sk8F7y6URsINVeUOwbicpKA4YetnXRfBlPTQIgGfV1YwsuULiy5V9O9QsndPgg1K1hlFt3XUByb1vARuM=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI0MjI4M2ZmN2QwNGJiZjJmZjhkZDM2MWJiNTUyN2Y0YTIyNWE0ODk1ODMzZDljNTc2OWE2NGYxMTYxZTU4MWY2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURHb3M4NGo2L21pRWkxR01JZVdid0hmcUpzNjAyS3FJeDhSZXNVeDZ1RFNnSWhBTXc0R1RtdzNtVGU3djlQVzJTT2M5c2NpU1NTUno0clB1R3kwYlVwcGhJNSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlpYcGpRMmx6TW5aVldraFNNRlpVV1c1TVpqVTFNSGg2SzIxQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlROTlJFRjZUWHBSTlZkb1kwNU5ha2w0VFdwRk0wMUVRVEJOZWxFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVUyTjNWWVkxZzBUbXRRVEZBeVRsTXliVU42YjFWTVpWTXdlVEJtU2pORlIzbHpPWG9LZGpkU00zbGFjVkJxYjBrMFRHZE5ielI1VnpWdFp5OUdOVkJ6UjA5bGNHNVhUR2xFTjBsSU5HcHNTVXd2ZWpscGVFdFBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUyZFZSVENtb3JLMlJqTjBGb1dFbEJhbUoyVDNWVU9ISkJkMjFSZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGYVJFRjNUV3BWTlZreVZUSlBWRlV3V20xVk1FMHlVWGxOZWs1cVdsZFJNbHBYVlRCWmVtaHJDbGxYVlRKWmFteHBUVVJrYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWWkdkR2NYTUtRVUZCUlVGM1FraE5SVlZEU1VkNllXWTBOMHgzZFhrdlFrSnlMMk5RV2xabFdtWndNSGxJVVU1NlozUlFWRU5HYlRGS2JDdDFjRnBCYVVWQmVqaFNUQW9yVkVWek9EQmxaSEpwU0VWV1ZrRnVWVFpPZW14dVNpdFJRM0UwWlRSamFuSnNWQzlMYkRSM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGUFNFVlNNMjVKTm1SSWEzUXhNbkV2TUZBM1RUbGtZa2czWTJOd1FrMTBTbkZFVDNJMWJGTkJlVkE1Y21kakwxbENPWE12UlVGamNIUnlORTEzYmtjS1VXZEplRUZMVldWaU5FWjFUVFJXTkhBM1VsYzVWR2w2WVhGS1VHeE1lSGx6UmtSQ2VtMTNOVmxhZUZWQmJuSnZZbXA1VFRoVVpITkJOalpSWTNwcldBb3ZiSGh6ZUhjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1671237255,
          "logIndex": 9249962,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "5d00259ce6954fe43d233ced6ee4c8dae6b9b07e",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3717579169",
      "sha": "5d00259ce6954fe43d233ced6ee4c8dae6b9b07e"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

