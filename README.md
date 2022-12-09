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
| `latest` | `sha256:460fd930225c326f0ebc2a5effdd4afaeb034ee37915532e77b512d9e37134e0`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:460fd930225c326f0ebc2a5effdd4afaeb034ee37915532e77b512d9e37134e0) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:460fd930225c326f0ebc2a5effdd4afaeb034ee37915532e77b512d9e37134e0"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "3532cdbed7fe7a45706adcb2be6f893e4f221c86",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIGHBGEvQZeoqDIISG4wL62oCbTJNWAiOV8qLWK6Shyk+AiAGWNnVHG0mc7T1etv+A+FA0mVTOU7kESlWffhnPmu3UQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxMjQ0ODQ2ODkxMGQ0YTkwNTAzNTM0MzQ0OTJiZjliMWNhZGI0NjNmNzNhODM2ZjE4ZDk3ZjIxYjU0MThjZjllIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUQ5OWd4YkFBTXN1QlExdzhVY29lQ0pLeEdSeWpBQnY5dmpFQkJKd0Q4Q3NRSWdIK0tYNjZNeUg3VlBtYVkrSlY0Wk8wNm9UWUI0dkRMaG5SYWpqS0Y5MXBBPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlZqbFNRMWMzVEhCTFRIQm1VMm80WW5KVlJ6bHRUa2xtZWtvd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVRWTlJFRjZUbnBKTVZkb1kwNU5ha2w0VFdwQk5VMUVRVEJPZWtreFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZMUXpoNWREZGFOVVJwVVRVM1RWaElNRVpNVUZwRWRXeE9kVGRqVTJwelVHcE5lQ3NLYkROUVpWRkdiRU5vZFd0aVJuZGhZalZWUVd4VFZVWnRUR1JIVEU1aVVWRnlRMEoyVkhOM2VqWnVXRE4yZUVGQ09UWlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyY1VWcENrRnNaRGh3ZFVsMmFWRkxRVGhyT1hZclNVWXZVMVpyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwT1ZFMTVXVEpTYVZwWFVUTmFiVlV6V1ZSUk1VNTZRVEpaVjFKcVdXcEthVnBVV20xUFJHdDZDbHBVVW0xTmFrbDRXWHBuTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVTUZWTlduSUtRVUZCUlVGM1FrbE5SVmxEU1ZGRFVGbzBPRUpFY1c5R2VrVlNkMjU1T0dreWRFWjBkSGhHUzFsMVFXdFVXVXRRWkRsbVZ6bFJWRWRGVVVsb1FVMTNlZ28wSzNOS2NFUlNRVlJ6YlRCdGNWQmpVazFqUldKRk4zRTVUV280VG1SVVozZ3ZiazE1VjB0RVRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlEyWnNjRUZZWTJZdlExUk5WakpqU3paRlEydE5NMHR1ZEZjd1ZUVnZaRkJ4VVRWTlZtVkZibFUxT0VZd1dTdHFWSFl2VDBNclNIWlZWVFZPWWpNS1dYY3dRMDFIUkhNd1dXaGpkWFZSVkRJeFpXd3hObGRvVkVaclpsVnBhR2g2UW1SMVdsUlphRVpZUTNacGNUWlRLMGQ0VUhOTGRtZzFSVFJtTW14dFpRbzNLMlZGU1hjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1670546267,
          "logIndex": 8695177,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "3532cdbed7fe7a45706adcb2be6f893e4f221c86",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3653349449",
      "sha": "3532cdbed7fe7a45706adcb2be6f893e4f221c86"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

