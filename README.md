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
| `latest` | `sha256:b266ba5578154991e3a19095103b50f5f0a5a80dc2a42a16034a669ec8eb78a2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:b266ba5578154991e3a19095103b50f5f0a5a80dc2a42a16034a669ec8eb78a2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:b266ba5578154991e3a19095103b50f5f0a5a80dc2a42a16034a669ec8eb78a2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "122e7807ee98bfa6a16496fd27630cf0d2df10c3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIGIM5GZ8qW9W0gdli4pRrOPDm9SJ8qQnuenfw3Y+y8rhAiEA8wp+mzzWU9U0MSksogGKpvi1xoYOvhJMRHsY4YQQrYo=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmOWRhY2IzZGVjMzE4ZGJkMWQ5NmVkNjIwODBlOGU0Mzc2NmUwODY1ZWI0NzI3NmJmYmIxNDkzMzc1NGMzZGY5In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUN6S3lsY3RadDRLTFNJWERJcHA5UmFhWFR5QmFqcUpIc2kwSTlXclY1K09BSWdSVngyUDhhaFdHNFlkZk0wemZKSlY3aEpIMHJHRWh5cE9Wckcva3kyZE00PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVlVWbG5lbE5FUzJVMVVVVTFSa1prYzA0MGFYbDVaak4xWnpSemQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUlRCTlJFRjZUbnBKZDFkb1kwNU5ha2w0VFdwRk1FMUVRVEJPZWtsM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZWTkhVdmFGTXhORFpuVjB4U2RYcGlhbXg1TlNzMFMwUnBZamxNT0ZwTU5tRm5PRmtLYm5SNU0xWnFVMmh6WW1FNVUxSjZXWEU0ZGtGb0szUkJiMUpTZFM5MlRqRklOMnhUUld0RVpXSkxaRzVEZGxWV2N6WlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZVTHpKaUNqTkJWRlJsTldwVlJYSTJTRUpuV1dOT016WjNNVEJKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoTmFrcHNUbnBuZDA0eVZteFBWR2hwV20xRk1sbFVSVEpPUkdzeVdtMVJlVTU2V1hwTlIwNXRDazFIVVhsYVIxbDRUVWROZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxWVDBWSUsyY0tRVUZCUlVGM1FraE5SVlZEU1ZGRGEwVjFVVTQzUm5SMFQwVkpNRGdySzAwMGIzZHVlakoyTkcxVFYxSnBNVUZoYlZVMWRtdFdVemh2WjBsblMxWkdPUXBuUzNCS2FuRnpObWxpWjIwdmFUaFhXRWg0VUdWTVoxcE1PRkJyV0RsQllVbE1VVEY0V1ZWM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGSlowTTFkbTkyT1RCcllWSmFWRlpFWVZwdk5YWjNUSEpGVld0Q00zQkpWRWhWYkN0Rk5HSlBiVW96WmpjMlYwbDFXVU5zWlRFM2FsZFpTbXhTVkcwS01IZEplRUZMWkhCbFMwcFlVazl0ZUV4QmVVWkljV0pYU1c0elYyNWtSQzlQWVRsTU1YbG1MM1puTnpsQlpGSlFkSFJzYlV4dGVtbGtOVXhhUkRjMFNRbzFiblJyU1VFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1670978274,
          "logIndex": 9040671,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "122e7807ee98bfa6a16496fd27630cf0d2df10c3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3690609636",
      "sha": "122e7807ee98bfa6a16496fd27630cf0d2df10c3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

