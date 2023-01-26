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
| `latest` | `sha256:0169bfc6909f9ca7361f4dd2d8d64922482a801ac1517c1837c595c89688082b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:0169bfc6909f9ca7361f4dd2d8d64922482a801ac1517c1837c595c89688082b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:0169bfc6909f9ca7361f4dd2d8d64922482a801ac1517c1837c595c89688082b"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "ea94143f66ca5f044c3310674b5a3e36335546d8",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDCJEorBhn3ULRLFORx3U41KSDOJGw63FZW2OMKAvZd8gIgaDH5wz8muRZ29iKfRVU9h5Cb+659eGHLGoY8a/HFWO4=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwMWU1YzIyZTcxZDZmNWNjOTFhYzcxNWQwMjc2Y2IwOTJiM2RhNWNkNDY2MzFkZDQ4Yzg0ZWUyNzY0NGVjODg5In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRTUvM0FtcEJjdlp3THhtWUcySDcwcFRnWW8vWXlBbDF4anVZTWJvdmdWS0FpRUFsNVNCcUQ0cHp3Q1BkbmJYVERScEs0b1VNbTE2RHBCaGtmN0UzT3luQ2FjPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCVFowRjNTVUpCWjBsVlJrVjZlRGRNT0hwMFEyWnRSRk01Y2tOelNWcEROMkZpVGxOWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVU1RKTlJFRjZUbnBGZDFkb1kwNU5hazEzVFZSSk1rMUVRVEJPZWtWM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZVYURsRVdqQkRUVWx4VFZGa1NqSnhTUzlVZWk5TE56Uk9hRmg2TUZCdmVrNVFWRlVLTldsUU1WTmFhVXRJV0ZKbmRGWXpNRXhwYlhsd00wdFNPSG93TkdkRFQxbE1hSGd3YWprMWF6SjNNbEF4ZG1kQ0wyRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUwY0hkdUNuUnNOWHB6VW1oV2IzaFlia1JyZEdOdGQxYzNabWxqZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd4WlZHc3dUVlJSZWxwcVdUSlpNa1V4V21wQk1FNUhUWHBOZWtWM1RtcGpNRmxxVm1oTk1sVjZDazVxVFhwT1ZGVXdUbTFSTkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxZY21kak4wUUtRVUZCUlVGM1FrZE5SVkZEU1VGbFNFaGpjR3RNU21OMFN6TldTR3d5VmpJNVdGazJPSGxKTHpoc2FUTlJVekJSZDJoclpuWXZjRGhCYVVGd2VGazNUd28xY1ZJeVpIQnVlbTgyUTAwNEszcHlRbVpUYldwbFNVMWFSbTFKV200d1JGTkNNVmxYYWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPY0VGRVFtMUJha1ZCQ25CT1QxQjZla0UyTkdFeFYySjJaM2hVTVdRMFJWcDRSMUZNVWxOUmMzUXdjVUpFZVhsQ1ZFbGpTbTV6VFdSM1FXOHlXRGRJTDNReldFcEpjMGxQZGxVS1FXcEZRVEJ6YldWcmRuQk5iVGxCSzJrM1dFZGpUa3hrTTNCQ09FRmlSblJpY2tnclF6Uk1iMk5sZUU1V1JsWkNOa1pyV2xKV1JrSkJXbVp4ZVhOUGVRb3JhM0U1Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1674693456,
          "logIndex": 11951836,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "ea94143f66ca5f044c3310674b5a3e36335546d8",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4011207824",
      "sha": "ea94143f66ca5f044c3310674b5a3e36335546d8"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

