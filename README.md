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
| `latest` | `sha256:201779a20f33b8e162993deaf2deb53c5896700c2679aff789fbef8ab950da3e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:201779a20f33b8e162993deaf2deb53c5896700c2679aff789fbef8ab950da3e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:201779a20f33b8e162993deaf2deb53c5896700c2679aff789fbef8ab950da3e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "8817dd2f69b8da34e89e5b74966bbfc0a545cdd2",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIHhhZThkZ+AVNBB1WiFqpyOuLjhkarf0zLo89bEndHlVAiBmGRgo0kgbn0iFhx5huijJNC550qYMHD+T3zjXJBlCDA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiNzU0MTZmZmUyZjdlZTEzMzAyMjk2NzFlMzBjOWMxMDljM2FmNzFjMzFiN2I3NDBmMmQzOWU0NzllN2Y1MGZlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUQ1c2M4cVp3N3RJc2lyNUhpOEZLSm9mYmxVaHZBUUxSWExBSlVwZm1mNS9BSWhBUHIvZnZIajMwMTY2YWN6bkNUb0llVEpvaC9YQnBackZTNndZQmV5MlZEYiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlMydE9WV2x6WjNOWFUwNDBURTVDU1dwck5WQTFTekZTVUVoSmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxUVRGTlJFRjZUbXBKZDFkb1kwNU5ha2w0VFdwQk1VMUVRVEJPYWtsM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZDZW1jelNDOW1abk14VFZVMlpVTlljMFpyYXpsWVZWZDFPV2sxY0dwbk1pOTZWRGdLY2xKNU9IVXpjRlF6YzIwMU9YZzRVbW8zVlc5Q0wwWjNiVE41TUVwb1ZXdFhOVU5yTnpFM2VrWnVZVkExVnpjd2FHRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV3TVRGd0NqVmtLMmxVVmtwNVYwWk1OREp5UlhKRGIzQTFjV1pGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpSUFJFVXpXa2RSZVZwcVdUVlphbWhyV1ZSTk1GcFVaelZhVkZacFRucFJOVTVxV21sWmJWcHFDazFIUlRGT1JGWnFXa2RSZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxVWm5Sc2FrY0tRVUZCUlVGM1FraE5SVlZEU1VST1ptUlNjM05VV1ZSTVJtOVlPVlU0T0VoV1ZXdEhhbUpGZGpCdGNVZzRURkJyYWpkS1drMWpVV2hCYVVWQmVrOWlNZ3B6VldaSFptZExlR00zVTBSRlowVnhhMmg1Ulhwd2NrUkhlVEpWYXpJclVGWlhNRzFyZDBsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTU5IcGhVek16V1VGd05WQmFWRmxSU205WUx6SkdTM1ZUUVhkc1NreG1jR0ZSUjBReFJFcERja2RoU0ZsVVUzbEtjMnRhYWtZeVNsRjNVR1ZUU0ZnS1MwRkpkMVp2VldSd1NqTnhTbmRZWW1remNDdHdRU3RWVHk5emRURlhLemswTjBGMFlsSnhSVU52Y0haclUzRjFjblZTSzFORWFtWnZjMEoyTjBSeE1RcEtkV280Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1670200612,
          "logIndex": 8419069,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "8817dd2f69b8da34e89e5b74966bbfc0a545cdd2",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3615839149",
      "sha": "8817dd2f69b8da34e89e5b74966bbfc0a545cdd2"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

