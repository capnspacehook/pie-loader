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
| `latest` | `sha256:31d2adacb31acd0e80a941df3868fbd6b804159bae0cd7535fcdbaf06c580a7a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:31d2adacb31acd0e80a941df3868fbd6b804159bae0cd7535fcdbaf06c580a7a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:31d2adacb31acd0e80a941df3868fbd6b804159bae0cd7535fcdbaf06c580a7a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "9f64989fe1d5f99227c5cd1cbda22693bf40b49d",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIECmJbhED75/6MHcA+YvwWKg3KfOrmAXowsv1We3oNUmAiBOfLdPTQEF4e1xMQ7iH342NzvjZU3MdAZ+bZ/iGfBl/Q==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjYTQwZmViMTUyYjZkNjIzMDg0NzY5OTUzYzM0ZTIwYTI4YzcxNGY4MjE0NjEzODk4YjZhODBiZDlhYjMxOWRhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQWZ1aG84TnZ2VG9jdmtRdkNRdG9XcUhFKzdGZkFNVi8wcHN2R0h6Nk80S0FpRUFsY3pLOEZHZ1M5MzJPWnlhT1dFemdTOFBRMzNjSGtaU3pncXdycHV4U2VBPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlNqQm5OMUEwUkRObVlqUlZOelZhTWpkQ1VYZHBUVVI2ZVVSQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1hsTlJFRXdUWHBSTWxkb1kwNU5ha2w0VFZSSmVVMUVRVEZOZWxFeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZETnpOelJEVkROVU5oUkVFek16ZEtVVEZCZEU1ME1rbG5XalJQWXpVMmVEQlFTMEVLV0dzMk5uTm9XVmRJZVRGd1lXVjNUV3RVYUhNeVZFUkNPREpsT0RrMU9XNTNPVU5zY3pScVdYSTRTVll5VjBFdmFXRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZyWWpKUUNtUTNlblFyY1ZWUVpXeFJjSGxrU1daMlJVeEtSMjVKZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpWYWFsa3dUMVJuTlZwdFZYaGFSRlp0VDFScmVVMXFaR3BPVjA1clRWZE9hVnBIUlhsTmFsazFDazB5U20xT1JFSnBUa1JzYTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUWTNsdWVUUUtRVUZCUlVGM1FraE5SVlZEU1ZGRVFtd3djUzh2U0c1c2RXNWhMMGg2VDJaeVVGUXJNbVUwUVdzd1NrNVRWbkZTVjJ4cVIzRmFZbEJZVVVsblprZ3ZUZ28yZURGVmVITlBkMUZGYVRWa05VWk9OMVpuWVdOU1IyWlRjalpZVkRBeVRtaFdjMEpMTURCM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGT1pESkNTVTEyYUVoMldrdG9VVVVyYURCcVJXeFdlWGd2UmtWbE5rVmlVSGw1WlU1V2RUWlFORVpHUjBGbWRXaERZWEJJWTAxaFoxQTBkVEpGTHpjS1dHZEpkMGRVYmpKYWVtaHBRa3BpYjBSc1FuTkpjemRKZUV0MVRIbFROSEZQWm1rclQwWlJOalp3TlVrdmFGWlZkbHA1ZVRoM1dVOHlZMkl2TTNCdlZBcFVVRzl0Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1669077858,
          "logIndex": 7578123,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "9f64989fe1d5f99227c5cd1cbda22693bf40b49d",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3519338594",
      "sha": "9f64989fe1d5f99227c5cd1cbda22693bf40b49d"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

