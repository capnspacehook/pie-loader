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
| `latest` | `sha256:a5bcd1d548e50e1df751680004f50c364371252dc52802a4556eb184488f3ac0`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a5bcd1d548e50e1df751680004f50c364371252dc52802a4556eb184488f3ac0) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a5bcd1d548e50e1df751680004f50c364371252dc52802a4556eb184488f3ac0"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "9bb45e281825c57bbe5f69206e80b9aa2b20ea56",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIGRNh0wAvamBbvJ04aLM7f/z4yNvesH1iT8Bc/+QA1XOAiEA2QM/0gdmq/vuc3MgF6Khk07XhUoZ27CTGCDooMDM4mI=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJkNTNlNDIzMDhjMDcxZjc0ZjkzODMzZDJiNTY0OWNlYzA0OTFkNzc0NDRiMjBkOGIxYTczMzY3YmQ5NzE1OTc2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQTh0YkdBek9WMkpTTEFleEdVaU9zRVhVNWdmMWVRaDUvRk9vTlpaeDB4c0FpQncrQUN6QjU2bHdXQlh1WjV4ZHZOaThOYmNFNTZBTW5GVVJsQWY1R0NBN0E9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNWRU5EUVRCaFowRjNTVUpCWjBsVlNXVlpZM0ZpVVd4ellVRnBhREJ6YW5SSU1tTnVOM1JYYm00d2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlhsTlJFRXdUVlJCTkZkb1kwNU5hazEzVFdwRmVVMUVRVEZOVkVFMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZXWkZSMlpHWnhWRlpZUzNwb1EzSnJTbFk0WmxsVmIyc3hjVUZJVEROVVprNWljV2tLTTJjMWJqVnJjSGRwU1dveFZHZHZTalJoT0hsb2VXZ3lORVF2YjFSQ2RYQlphMXB3UkhSWE4yUlVlU3RsWm14UE1uRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ4U1ZSMkNrMUpXR0pvZDNZemMxUlNUMVUxUWt0WlFtazVOMlU0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWWmJVa3dUbGRWZVU5RVJUUk5hbFpxVGxSa2FWbHRWVEZhYWxrMVRXcEJNbHBVWjNkWmFteG9DbGxVU21sTmFrSnNXVlJWTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhUkVWWmF5c0tRVUZCUlVGM1FrbE5SVmxEU1ZGRE4wbFVNV1V5YldsMFlUVTRiM2gxVFM4MVFXdHRSMnh4Y0dnd1ZGaG5ORTQzZG00eU1EaGpiRTVCVVVsb1FVcFJTQW80YVdsUVRtSTBjVXRTVUdGak5IWmpXV2haZVRaaVIwTjNZek5rZFVoYUwyTndja0V5TkhFMlRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeWEwRk5SMWxEQ2sxUlJHY3ZTVE5oV2tKRmMwOU1Ua1ZVY2tjMmRqUkhaMlJOUzFWQmRrZHpUVEZMTHpCeE9XVmtjWFZDTlRaaWRtaFJhQ3RDSzFBeFdrbGhMekEyY1VjS09EbFpRMDFSUXpCRldFVjNhblZVTjA1eWRGVnlZa052VkRsQ01uWmtlSHBKZWpsUlQxTkhjbkJQYmpGbVoyRXZlakZQZFc0ekwwMUNRV3RhT1d0TlR3cGFha3AwU0dWclBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1676162487,
          "logIndex": 13145268,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "9bb45e281825c57bbe5f69206e80b9aa2b20ea56",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4153890843",
      "sha": "9bb45e281825c57bbe5f69206e80b9aa2b20ea56"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

