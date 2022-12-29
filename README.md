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
| `latest` | `sha256:45d6ca8c2a7684329cc5a77c4d48df26aa86c3ff96e1cf5e2fcdb1984581704e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:45d6ca8c2a7684329cc5a77c4d48df26aa86c3ff96e1cf5e2fcdb1984581704e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:45d6ca8c2a7684329cc5a77c4d48df26aa86c3ff96e1cf5e2fcdb1984581704e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "56daddf27f09c506425fde4c9d294572530992df",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCICE4XD/A2RZpdQQckJACuyz/ERVRGox8ip2mHM/IHm7eAiEA7aPENWQFV+ZA7N/DapizxNa1dVZwKUavuYeNMnOXQOw=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJkZTI1NDEyNmRlYTU2ZDJlMjMzY2Y1YTk0NDE2ZTYxYTNiNmVlZmNjODVkNjBlOTAwYTE4NmI0NGY4NjkwYjYwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURSSVFlaUNOaDI2bmdyMjNlREY3L2dKZlFNa0hRRGIyemhxNDcvOFlTQVJnSWhBTEFVWWs1eHoxN1hNMnVuelUxWU1tUjAvWU1Sb3ZscGVGbDlEc2ZMRHlOSCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCWFowRjNTVUpCWjBsVllUaFhUV1JIU2pCWVFVcHVSekF6Y1VSWlRrcGFUMkl6Y1ZwQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFxU1RWTlJFRjZUbnBKZUZkb1kwNU5ha2w0VFdwSk5VMUVRVEJPZWtsNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVY2VHpJd2VGUnFkbmRYVTNWb1NXVkhVRVoyYjJaRlExbGlNR2xxZW1VMmIzTkRURGtLWm5ZMFNFRkJXa2RDY214Q2FUaFBTVFpPTDI4eFRUZExhaTlWVEhSRFlscDBTbmswU3pOMWNEazNOMmRzUjJaU2VIRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZsYnl0MUNtczBhbFZwY1ZwaU9UQnplRzRyVjNOQmRVUlJaV04zZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGT2JWSm9Xa2RTYlUxcVpHMU5SR3hxVGxSQk1rNUVTVEZhYlZKc1RrZE5OVnBFU1RWT1JGVXpDazFxVlhwTlJHczFUVzFTYlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxXWWxRcllVWUtRVUZCUlVGM1FraE5SVlZEU1ZGRWNrWTRVR0phUjJGSU1GbHNNbTl2YlRGSldrRkljSEJMYUhKTVMyTTVSMWxYWXpKNldYb3dUbGhpWjBsblNWTkdUd3BrY0VkVlVrdEhWbWxRTkhWWVZYZG1iVVF4VFVGaFpXNDBNMDR3Vm1SclJHWkhNV2g2ZEUxM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGUlFYZGFaMGw0Q2tGUFNsQm9ha1F4WTNSaE16WjFhbXRCWVVST1VrUnlhRVIzVUVaR09XeE9UVkZQZUhGVU9EQktZV3c1TUdSNFRHeGlNbE50VDIxSVRXcFZOMUYwTlZVS1NVRkplRUZMZHpNMFdWTktja0pVT0hjeVVGWjBVMVZ3ZDBoRWRtUnpTV1owY25vNGJ5dFJhR2RXTjA4M1VteEhWRmRSV1c5UGFVa3paVGxHYkRORU1Bb3lTUzlEWldjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1672274262,
          "logIndex": 10043825,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "56daddf27f09c506425fde4c9d294572530992df",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3797440845",
      "sha": "56daddf27f09c506425fde4c9d294572530992df"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

