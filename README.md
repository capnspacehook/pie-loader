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
| `latest` | `sha256:16b269da892c7294e4f5a9ac9d1cd5c0cedee824e4e638e675156a9bfbb0aaa1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:16b269da892c7294e4f5a9ac9d1cd5c0cedee824e4e638e675156a9bfbb0aaa1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:16b269da892c7294e4f5a9ac9d1cd5c0cedee824e4e638e675156a9bfbb0aaa1"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "5f8e6ae9321bd1a2f4ff63bba9ead6cc4f487bf3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQC1OluZtzAMBsYUdNl+LgxFDkZqH4VaAsUWTpT+PdteVwIgeRKPJZAmgBBXDD5cRpZf/Tl6O127YO1sOuofqGsUiEg=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzYTIzMDUyOWI0ZjkwMmMyYTRkOGNlY2VjY2RiMDc4NzliNjRjNzVlNWVhMGNlMGJiMjRjMjJlZDA0NTBjZGQ3In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRVFuRko5QVh1NFA3OEJPN2w5Tk9keWo0THVQWVg2N3BBK1krNVNLSlk2eEFpQTdkdzd2QWxGdVdOUE5qL056QmVIb2ttWHQwV1VFZGJ3ODVGeURGdWlkdHc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlRsZHFLM2RyZEdsQ2NscG9URGQwVERKc1lWZGhRa2x2YldFNGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1RSTlJFRXhUV3BKTVZkb1kwNU5ha2w0VFVSSk5FMUVSWGROYWtreFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZtYmtGQ2RFczNWbXBvZEV4dlVWTllkSGxqYTI4dlltazVWRGxOTTFZNVRrbHlTak1LWTJFNE0wcDVkRU5vVVc5NmEyUjJlRXRwVWpGTlVIVlRPQzh2Y0dGM1pWVktabFpGZEVaMk0zSm5TMVY1VEV4Mk5HRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZQTW5wakNuUkNUMUFyYUM5WVJWbElTRVU0UTAxTGRVcEJZbEZOZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGYWFtaHNUbTFHYkU5VVRYbE5WMHByVFZkRmVWcHFVbTFhYWxsNldXMUthRTlYVm1oYVJGcHFDbGw2VW0xT1JHY3pXVzFaZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSWTBVeWVua0tRVUZCUlVGM1FraE5SVlZEU1VVNWVFMVhXbFZMU1hOSWRtOVVkMFpUY0RSdmRVOUNTbkpMT1dzNGIwbEplVTExZG5ONU5FVk1RMlpCYVVWQk1uRkhLd3BzUnpCaFZUWm5halZRY0RGelQxSkViVUZKWXpSa1kyVnZRbGswVjBoWFprUmpkV05NY0dkM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTVR6WlhjMGt5VFc4MmNFZFZZbGR1T0VGaE9Ea3lkRkUzU0ZsWUszbFJhVWQ2VmpSU2VXYzJXSE5yVlhCVkszaEhiM0F2Vkd0VGFpOTJhWEZJY0dnS1RFRkpkMVJQT1d3NVpUTlNhMjFNWjFoaVlVbHljM2RDZFdkalVUbHdiWFIxUzFGSE1VSmFNRmx4UW5saU5FZHFRVEkyYVZKbllrSm5aMFUwTURReVpBcGFSblZEQ2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1666918371,
          "logIndex": 6013351,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "5f8e6ae9321bd1a2f4ff63bba9ead6cc4f487bf3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3341981976",
      "sha": "5f8e6ae9321bd1a2f4ff63bba9ead6cc4f487bf3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

