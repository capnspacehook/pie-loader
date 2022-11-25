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
| `latest` | `sha256:a55faf2650797d357ae9d75933776b599bb29a11e42116fdc9f00fb7d627bf59`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a55faf2650797d357ae9d75933776b599bb29a11e42116fdc9f00fb7d627bf59) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a55faf2650797d357ae9d75933776b599bb29a11e42116fdc9f00fb7d627bf59"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "75ebd790d010086c14ecad5764c9f9472b4c0fee",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIC6KzGW8dj8PM0Z0IUNydQYiiFo0HlSioZVKL0xBTu2oAiEA+jbrd7DVcCkU9Kh4NOZIMj8ar4aJd5dtq7JP+j6XEIs=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiY2Y2Yjk4NjAzMDM5YTJhNWZkZjMxNzEwYzQ1ODNjNzJkMTFmMmRlZGVmZTY2MGMzNjNlY2E1MWI0NTllNmM0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRWdYTWZSZk1CRGJCN0dPNWR2dUtvUUVSQms1dXhhNktGVGhTMjdHV2N2c0FpRUF6RG9heGFNbnZFRXFta0c5amZ6QnZyTThKZlFuSmVYQWxNS0NUQy9LdlpnPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlduVXJibkpaTTBWME1YRkpkWFZKVWt0V1YyVjZlV0p4VW5WbmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RGTlJFRjZUMVJKTkZkb1kwNU5ha2w0VFZSSk1VMUVRVEJQVkVrMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ0ZWxGTFVtVlZXbUp3YXpBMlZGbExaVkJTY1U5YWJrMDVVSGc1UVcxTE1IQllWRlVLV1ZRek1tNVBaaTlEY1d0V2JXeENXR0Z3Wm04NGNHeFZZMkpKVTBGdk9GbDFZVEJaUVU5c2JreDRNREl6S3pGM0syRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ4TjJoeENqQXZXSHAzVFVZcmRXNUxWMjVoY3pkdlV6RlhXRzkzZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOT1YxWnBXa1JqTlUxSFVYZE5WRUYzVDBSYWFrMVVVbXhaTWtaclRsUmpNazVIVFRWYWFtc3dDazU2U21sT1IwMTNXbTFXYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUYzA5aFJITUtRVUZCUlVGM1FraE5SVlZEU1VNeVVHVTFlWGRHTW00eGMxSkZPVVl6Y1hkaVNubElWRVkzSzJwdVF6TmFjVll2TjFoSUsxZFZlV1JCYVVWQk5GaDZid3BXTlhaemFGaFFaVVF4VUZsRGQzWnRXWEIxV0UxaWJGbFViRWhIUjBoWmNuWjBTR1V5UmpSM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2xocFIwb3dVM2hhWVVzM2IzZ3dWMDVSU2pKNFRtdHVjbFE1V1RWcU9Hc3hkbFowVTFkVlJVRnllRm92TkdOTVdrbEphV0Z2VEN0b1IxaE1NMXBRV2t3S1FXcEZRVGcyYUV4Tk5qUlNhMm95WTJVMVRrWkVVbGw1VEZGMVYwcHJTbFpyTlROYVNEQmFUVmRuTkhoVWMyWlBNMDVYV0VjM1YwbHFXR3h3ZW5jcmVRcDFWVk41Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669336788,
          "logIndex": 7792863,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "75ebd790d010086c14ecad5764c9f9472b4c0fee",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3544452010",
      "sha": "75ebd790d010086c14ecad5764c9f9472b4c0fee"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

