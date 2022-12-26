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
| `latest` | `sha256:037ce6354cb1cd2678893fa7fc7e80905d0420cc9910ee873f14ccded4778b85`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:037ce6354cb1cd2678893fa7fc7e80905d0420cc9910ee873f14ccded4778b85) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:037ce6354cb1cd2678893fa7fc7e80905d0420cc9910ee873f14ccded4778b85"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "a8d988359616b547aaf1e8b95f4862d663900180",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFVwX9aJINYJPCqyL5NXrG4ryh5/YJmZ92DC8SvA2xC9AiEA/7jIWvixoBxA0gyQGDOoXlCd4NPnDdSdY80rcQpv9VE=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlYjgxNWMwMGVkMmVjZDllNjE4MTMxNjMxODQ4N2I2N2FlMjI5MzQwYzE1M2JmNzIwM2U4Yjg1ZWZlODgwNGVjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJSFA0UXVqU09EZENFTlpJUGtjcnRZUll2VWhUNS9BZFBsdmpWbTFEd0wzOEFpRUFwRmFsdzhHUkVZZUI2a1FGVmFlTFphVTlUR2VqKzhnMUFZcHh2RjN6M1dVPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlVVUjJlVE5SWTAxaGVpc3ZiR041WVVSVU1UVlVVMHhxWVc5bmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1RKTlJFRjZUbXBOZUZkb1kwNU5ha2w0VFdwSk1rMUVRVEJPYWsxNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVY0YTBNdmFEZ3pZWE5RYUdWR2JYTXZjWGxvTkdsTlozQnRaWGxMV0c1dlowTk9OakVLWnl0NEwwNUxkR3BrYTFkS1NsUnBUbTR4UkRadFl6STBRbFp4U3poTmExWjRjV2hXVW5kTWNFOTJWMjVyVURGUlVrdFBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ4YkZReUNscEtkblYxYlNzd01HNVhSV3BVZUdNeFVFUnRaWGs0ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdoUFIxRTFUMFJuZWs1VWF6Sk5WRnBwVGxSUk0xbFhSbTFOVjFVMFdXcHJNVnBxVVRST2FrcHJDazVxV1hwUFZFRjNUVlJuZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXVEROQ1FWZ0tRVUZCUlVGM1FrZE5SVkZEU1VVeU1rcFRORmRQVWxWalowczFOa1ZpVVZWcWVpOXVSMUpMUzJkMGFubExWR3dyVmk4MlZWcDFlRlZCYVVGT1FsbFJaUW8zZW05UU1ESTJZMlZRU1VkNlNHcDBUMHh0TDBoS2NtaFVSamRMYUV3NGVHeHhTVlZOYWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha0oxQ2tvclJrbFBhbXByUTA4NVUzbERkUzlqUnpKRWJIVkdRbE16VDBGblluTk9Ua1J6V1hWV1lsRnVUalZCTVhKYWExQlJUM2xqYWpGMU1EZzBhWGcyTkVNS1RWRkRTazVFYlV4RlRrbGFOMkprUW5oNlRuQmpjMlJFVUVOVmNWSlhNakJtSzBsblEybzJkbHBZTldWbWJtRlpkVE5uZVhWd1YxRXJPVUp4VGlzdmJ3cFliWE05Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1672015015,
          "logIndex": 9841680,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "a8d988359616b547aaf1e8b95f4862d663900180",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3778133008",
      "sha": "a8d988359616b547aaf1e8b95f4862d663900180"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

