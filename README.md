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
| `latest` | `sha256:3a85f33a962c7a389e10cc4959c64e5963eeca050d1caf90cfed03f6313672c4`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:3a85f33a962c7a389e10cc4959c64e5963eeca050d1caf90cfed03f6313672c4) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:3a85f33a962c7a389e10cc4959c64e5963eeca050d1caf90cfed03f6313672c4"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "04a104ea2fcaf089c22af79940011a93af6def57",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDg7syf9o8MEMyG1FPomOlMl/poZfI4fSqNaaEaW8cMUgIgXcaJkxm9iBreI+/7xvPifr0NRP3CjSqJBmicFMwXqug=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlODAxMzIxOWZmZjExOWZjNDU3OWNiODM0YTdhMTg2ZDAyOTNiZjdlMjkwM2NjMWE3ZDAyNjAzN2Y2N2Q0Y2NlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJSFB3UlgxRVk4aUxFcUhIRlBZbUhtOCtBaW1hUFpDTGhITnlSMUgxYXRIWEFpQTZ4MXdHVUhxMzlYUkVYekVWWHBDc3Q1TXlkWmZFL3ppandDaG1kT296b1E9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlYxWlBXbEo0Y2lzemFIQndlRnBaU21Kek0zSkNWR2wzYjFkRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1RWTlJFRXdUVVJWZVZkb1kwNU5ha2w0VFVSSk5VMUVRVEZOUkZWNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYxVDFsNE4xbEZiekZhTlRKWGFGTldhVE55WVRodlRWSmFRVEp4WTNFd2VXUkRXRTBLVW5WaWFYTXZWelJ2VGs4MVkxVlNjVTExTlhVM05DdDVNVnBXZHpkUlMwWmpORGhHY0haNFlXTkNVMU12U2pSb1NqWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlY0WjBwckNrcGxVM0JxYjBsV0swcFhVRUpWYW01SFFXZEJiazFyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNkT1IwVjRUVVJTYkZsVVNtMVpNa1p0VFVSbk5WbDZTWGxaVjFrelQxUnJNRTFFUVhoTlYwVTFDazB5Um0xT2JWSnNXbXBWTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEJTVmxLVEhkTFJrd3ZZVVZZVWpCWGMyNW9TbmhHV25ocGMwWnFNMFJQVGtwME5YSjNhVUpxV25aalowRkJRVmxSYUV4NlZWTUtRVUZCUlVGM1FraE5SVlZEU1VKM1puQTVkV2xOWlRWVlFVRTVjRTh2UzJKeU5tWXdSRXBXYWtGV1JqUmlaVWRaVFZWbVExTmliakpCYVVWQmFWWnNTQXBXVm1ZdlVtSkJTa2RXT1U5bE9WWTVhVkl4VEhOa2JtNW9SQzk2YjA1WlluWTNUelJtTmtWM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWwzQ2xWRlNsUmxUelU0UWtsU05EUkJVR2R1YW1wR1NEUlhhbk5GWjI0Mk9VWk5XVzVIYWpCWVl5OHJNMkZNWXpOUFdXOU9SemRaTWpaUWFpdGhSMlZuYVhVS1FXcEZRWHBLTmtSUlQwcDZXVlJzUkdWR1lVdEZhWGhTUzA5WmF6QjJkRXBtTW05TFpUa3JRak53UWpSV1REbHlMemw0ZEdaa2RVdExjRTAyYVRkbk5BbzVhRUo0Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667004071,
          "logIndex": 6072573,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "04a104ea2fcaf089c22af79940011a93af6def57",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3349424047",
      "sha": "04a104ea2fcaf089c22af79940011a93af6def57"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

