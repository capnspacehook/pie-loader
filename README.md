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
| `latest` | `sha256:bf73b7242db23f45c0ba35658d33fa5e7d828f8c6a0726444edd4eba97501a43`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:bf73b7242db23f45c0ba35658d33fa5e7d828f8c6a0726444edd4eba97501a43) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:bf73b7242db23f45c0ba35658d33fa5e7d828f8c6a0726444edd4eba97501a43"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "22ea8c8ee23cfd19ee3762bcb5da4cf87a15e4b6",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCICnKnBSU9XP4nckui9uu7Bq+xKk8uqfL2mNjAOEn8ssTAiB/o//w+I2+Pwwky+Rsd+CLroHmEmghzKEGwm90dhtRcQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI0OTI3NTZjZjUwNjZjMTc2YWE1YTFiMzU4MmE5MDRhOWEyMjg2NDIzMjMxNDRhOTRlYzE3MGUyOTU4MGRiODFmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRTBoWkZDUXFmK2NNZmRFZCszbjM2ZzlmN2paekxpRDFRMVFNd3YzQjJrK0FpRUE3a2J2bmMyK0RIZHhhUDgrTVdqV1BONFFzdXM2eXg1eVJpRU5PV0NQeGI0PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlJGTmlNMjE0YlRkSmRubHhXVlJTVkZwa2MxWkxMMGxRZVVoM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1hwTlJFRjZUbFJSZWxkb1kwNU5hazEzVFZSSmVrMUVRVEJPVkZGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ0YVdsREsyOXVZalpDWjJGTk9EUnVNWGxyVjI1RlRXUkxOblUwYlZZMlowNXJhelVLUjBaQ05sUm5kbFJLVWpOWWQwdEJSMlpFYjBoNVkwWmFaRXBPTld4RVYwVlllV1YwYjFWelQwaEtWakp1TkZoMk5XRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyYUhaMUNrOVFVMlZWTkRSdFZ6TnpVMHQ1YlV4amEyeFBORlIzZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsTmJWWm9UMGROTkZwWFZYbE5NazV0V2tSRk5WcFhWWHBPZWxsNVdXMU9hVTVYVW1oT1IwNXRDazlFWkdoTlZGWnNUa2RKTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZWTBSWFdITUtRVUZCUlVGM1FrbE5SVmxEU1ZGRGNUVjRMMWwxYTI1dmFIVjJVV05JYzBKS1UyOU9NR05QTjNOT1R6SnpOMUZTUlhrNFpYUjZRVk16UVVsb1FVeFVPQW9yVDNNclZUaDJiV1Y0VjJKdU1GYzRZV1ptUVhrMVVUUXdURzFIVFRKbGRFWlZVREo2TVhGaFRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxR00xVnBZVGQzVGxBeFkwdDNaaXR4U2xNd1UxTkdWelp6ZFZGV2RFUkdaRGdyT1RoTFVHRkliMDVRUjNRM2JYQlhhM0ZUVG5KM01XRm1UMUJ6YUVZS2IyZEplRUZKYjJZclIzQk5jMGxHYTJoalYySlBMMFF6VHpOd2FYVm9TSFo0TTFVdmVtbHhkMWd5TDFsWmQwZDZlbWwwZFZod09IY3hWbXhaVURjd2NRcFhPRVJPYUhjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1674434163,
          "logIndex": 11738187,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "22ea8c8ee23cfd19ee3762bcb5da4cf87a15e4b6",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3982320007",
      "sha": "22ea8c8ee23cfd19ee3762bcb5da4cf87a15e4b6"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

