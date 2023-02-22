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
| `latest` | `sha256:7e065f2de45c142f7d771894c39dd21c04d4e2a4d95c7b41fc5aa770bf3e24a7`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:7e065f2de45c142f7d771894c39dd21c04d4e2a4d95c7b41fc5aa770bf3e24a7) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:7e065f2de45c142f7d771894c39dd21c04d4e2a4d95c7b41fc5aa770bf3e24a7"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "9b5e4329c3ee9dca6bf920e3cdf7fcd74be73aa3",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQC9kXcqEd64v/Xk9RF7J/PBtOjXo/CsJLkB004dPhbRDQIhALRb/aO3ZaxT0U63lxd0h01aSMH9qWLnmjFIgGW5Ba/K",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3YjI2MDAzOGU5YWRmODNmNTVlMDRkNzI3MjNlY2I0NGQ4NTFhZWM5YTAwNzkwM2ViZGViZjViYTQ2MjllZDdiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURkN2xZb2Zna2pYbVU1MjN0SEtVOGRmVmhnbDRNdlZBMDBhZnBlT3labFFnSWhBTG1ibUxBa2lOdlRwMzBWYkZhTHdqZUZRd2pUendFNkFqTTlKOXBtcFk4eSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlFVbFVaM0J0TW5KR2JXbE1TM2NyTVM5S1lXSXdObVlyUzB0UmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxU1hsTlJFRjZUbXBOTVZkb1kwNU5hazEzVFdwSmVVMUVRVEJPYWsweFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZNUTI5a2VFcERlbEJyY2xGcVkybFRUbUpsY0ZKWVVIRjZUbmhaYWxKRU5HdFdTMHdLWXk5emVERmpaV3hITWxoNWNsRjZOM2RSVUd4dFpWWkRNa1E0YUhoSFJFeFNPRmhzUW5SUlIxSmtUMnN3UW1semVqWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV6YUZneENuaEhaRWxYYldOSWJVRnpORmcxV1ZoRFNFaENRME5uZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWWmFsWnNUa1JOZVU5WFRYcGFWMVUxV2tkT2FFNXRTbTFQVkVsM1dsUk9hbHBIV1ROYWJVNXJDazU2VW1sYVZHTjZXVmRGZWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhTW1wUVpIRUtRVUZCUlVGM1FrZE5SVkZEU1VoTFQzQkVlbkZEUlVocVdIQjRhVUZaWVhVeGVtSTNjSHBpZEhBMlFuZDFZWGt4ZFVKSVpuaFdNRzVCYVVGV1FqRlJlZ3AwTmxWVEsyOXVRVFppUjFOTFZYZ3ZTV3RqVjFOS09VdzRjRlpGVFROSVl6UXJUbU0yVkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ25ReGJ6UkpUa1JyVUV0MVJsaHlPRFUyY0V0MksyWTFlakJXZVROc1JXbzRTMGhIYnk5alN6Y3ZibkoyUkhsR2VsRjZiM2M1WXpCTFVucDBkRTVJY3pjS1FXcEZRV2hIYkVWM2QyZHhOWFZOTjJsWFZGTlViRWhWTDFRMldscHFVVTVIUjFWS1UzSkllSGN4T1VabFFpdHVWakpHTUVKeFRXeHVhMkppUVd0YVVBcFlUa0p0Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1677026219,
          "logIndex": 13882282,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "9b5e4329c3ee9dca6bf920e3cdf7fcd74be73aa3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4238181476",
      "sha": "9b5e4329c3ee9dca6bf920e3cdf7fcd74be73aa3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

