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
| `latest` | `sha256:241593bbfc1143a16a49e9e11e0fbf224279a14e9e1b9fa15c80719f96c5aae9`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:241593bbfc1143a16a49e9e11e0fbf224279a14e9e1b9fa15c80719f96c5aae9) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:241593bbfc1143a16a49e9e11e0fbf224279a14e9e1b9fa15c80719f96c5aae9"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "56b8d01300b21e8483f0f9cad99979c4583ea715",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCTQxubJie8r55LHF0N0lHxw5w7SH4zQb5PLGAp2KxISwIhAIz+3xF0NeoCQjXqTp4FKaXqbAQQjjDzc+EIza8/9ocX",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4NzM1MTYzNDAyNDc1Y2VjNjlmODE5OTYyNzU4ZmVkNzkzZmU2ZDhjMzIxOWRmZjhkZWMwMTc2YTk2M2ZhNDJlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQkpKalBCTHpNQzhITnJPU0h1ME92Z2NFeUN1YmlwZWZQR3FMbzFwUzN1MEFpQlJhZlZWOFE2YURORnBDZ1AyT1d6VHVSL2c3SmF1YzNvTG9NZ2dmNWdRNlE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlFVcGtRV2d6VFRacVJuRjRibk5pWlc1aldXdHhUM0IyUW5nd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1RCTlJFRjZUMVJKZVZkb1kwNU5hazEzVFZSSk1FMUVRVEJQVkVsNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYxYm0xRGFrZHdTRGwxZFdGUmIwOVlabk5yUzFoYWVHMW9ZVk5ETjBKS1oyaEdRMU1LWjNkalVWUlZZbEZRVG5RclRFeEpiRWRITVZBMFpDdFlZV2N6Y2xGM05HcDZaemxoWW1rNFZHbEVUR0p1TURGSWEyRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ0UmxKSENsWlhVM2x2VGxkcVRrTTNUR0pxU1ZoRVdtWTBVMWwzZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGT2JVazBXa1JCZUUxNlFYZFpha2w0V2xSbk1FOUVUbTFOUjFrMVdUSkdhMDlVYXpWT2VteHFDazVFVlRSTk1sWm9UbnBGTVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZYUU1NGFYTUtRVUZCUlVGM1FraE5SVlZEU1VVeVpURnBWM2t2UkhsTlRqRm5XbGxuTmpOV05VVlRaM2R1VERCNmJWcG5hWGxKTm1WdWJqTkZhamRCYVVWQmVtRmpWZ3AwVkVoRGVteGpUR1owWVVGa1UwTmpiRzlLWmpKV1JGUXdkMVZNVkhGNFlWQXpjbVpNVWtsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGSksxUkRSMDVXSzB0VVQyUkRSVTVWTW5SVWNtZFZNbFpHVTJVeVdGSllMMjFxVEdWak9WQm9aRUZsZFd4S05tNUlSWGR3ZUdOUGRFeFpOVFpoZUVVS1JGRkpkMHBtWjNoMmNWZHdTbFF6TnpGVk0wSlpUVTlpZGs5WFl6ZE1XbmxvY2xSWldXVk9ObkptTmtRNGVtNVlibUpVV0V4WlVEbFRSV3haT0hnMlZnb3hWU3RrQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674520786,
          "logIndex": 11810546,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "56b8d01300b21e8483f0f9cad99979c4583ea715",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3991878199",
      "sha": "56b8d01300b21e8483f0f9cad99979c4583ea715"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

