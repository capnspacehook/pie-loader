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
| `latest` | `sha256:fe4e673fad66a57b2f7c3925ef9973c40c14c04202ab76d430cdb069c2c7342e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fe4e673fad66a57b2f7c3925ef9973c40c14c04202ab76d430cdb069c2c7342e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:fe4e673fad66a57b2f7c3925ef9973c40c14c04202ab76d430cdb069c2c7342e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "01487306834378be2cabd7b324195e0bfe166045",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIEnHRSo/xU5RxEZyuzBSXXJzQVZp5Z/N7e4RvPTvXukGAiEA8cNP1Xd53QypSRhiUgwPwsHW7fWHhyAB0S+BoLy6dBI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1M2JlYTllNmY1ZmQ0Y2Q3YjA4NzlmMzFkMDcwYzExZDMzYjJmM2JkYWY3N2I3NmZmMjFhMmRjZGNmOTEzNjMwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRUFlSzVLWENXa0M1dGpZanpGNHc3SG9TVWU4VU83OFRWNDhacnF4YzBScEFpQmtaTUFtRmg5bDZnTkNCc2VHUSt4Rk5ZNlNTVnVhTjZwejFFSVJCT28rUVE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVllXa3JjbVEzYVUwMVZEQnFNbXAxZVZOV1NXZzNTemxvV1hsWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1hkTlJFRjZUMFJOTVZkb1kwNU5hazEzVFZSSmQwMUVRVEJQUkUweFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYwZDNCa2VtSnlWREo0UkZaaVRrSmlaamhsVTBSVllsSXlTR05USzJ0MWRVUjRSbThLV0ZsT2JESkZMemMyVldwdVV6VnVabUpxUzNkUFdpOXJabTFpWkhoUUsycFRhRVpJTnpWUFZqUlVXVXR3TldoYUszRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZOT1hWWUNqQjVXSEJQYjIxVk0wSmhORGxMTDBwNVkzRkVaVGh2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkTlZGRTBUbnBOZDA1cVozcE9SRTB6VDBkS2JFMXRUbWhaYlZFeldXcE5lVTVFUlRWT1YxVjNDbGx0V214TlZGa3lUVVJSTVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZVFc1UVNDc0tRVUZCUlVGM1FrbE5SVmxEU1ZGRVltbEhlV3RRZEdaWVpEZEZOMDVyTjJjdk5YbFpXbE5HZUZSWGJIVjFUM2ROZUM4ek5Fd3hPVzQzZDBsb1FVczFid292Y3pJMlVFeHFXVTF2VUd4VFdGRlJOMnhsWmpOM1UzcE9LMHBLVDBOM2FFSlVRbkJOTTNwS1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlExQkxlV3M1TURacFVVdE1kV2hqVjFSVWJ5OXpUUzlJUnpkVE1Hd3ZRbXhWZVhwdUsyNTZZM05SYzFaVUsyRTNialpOYjJsWlVVUnhlWFl6YzJVS2VYQnJRMDFIYm1wQ1YycGpRbkpQVm5wSk1tTlplR2xDZEVaS01WcEdLMU51ZGtaaFZYRjJlWGhqWVhObWN6bGpTV3BtYlRaT2NVTm5hVU00WkVkMU53bzNVV2N5SzJjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1674175138,
          "logIndex": 11547906,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "01487306834378be2cabd7b324195e0bfe166045",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3963646627",
      "sha": "01487306834378be2cabd7b324195e0bfe166045"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

