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
| `latest` | `sha256:8f4fb4b553437a7540389eff27d940852b104c6ad6cbe69eb92d03c07fb24d98`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:8f4fb4b553437a7540389eff27d940852b104c6ad6cbe69eb92d03c07fb24d98) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:8f4fb4b553437a7540389eff27d940852b104c6ad6cbe69eb92d03c07fb24d98"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "e5ec7965ea98d70909788ee3faf122f9da2950f7",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIG+twHL4/kkBKcYBP9wIyfXPiJRSZJ9bjNkvha69G0VTAiEA1kQHlV1+cMBxtXRCITZbG45fFlelXoGCJEJQzmqvj+g=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzNmRhYjI3ZGNhOGRjMTQwMDdmZGY1NjNjYTY3Y2ZkMDRjNjI5OGI1ZWY2MTMyODcxOTg4NWEzOTJiYmZjOWFhIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNtdFdkQ2s1NDBjN2h5aHl0ZkJ2OXo5UDNiQlpjVW5XNytjZk9aOTlHeXh3SWhBUGc5Z2JyMFNBVnlHSkVmMFkrKy9QdVB1MGM4emhodjRQMXRhUTdtZUVNbiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlZXZEljMWhPTVhsTWNtSjBlbHBCV0VwalkwVlVNMWhQVlhWbmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlRGTlJFRjZUMVJGTVZkb1kwNU5hazEzVFdwRk1VMUVRVEJQVkVVeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZZWldwemFtOHljQ3RDYVUxcmVHeEZNbGxJTHpsMWJGWXhRa0V5WWxKc2Jsa3lVMHdLVUdsVVVWYzVlazVoWVRkc1prazFVVWRtTTJONU9Tc3dPRFJhVTBaWFMwUmhOM295UVVwc1V6RTJZbVZUVWxoRE5tRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZSTWpOU0NsaHhhbWQyWnk5SFdGUklhMnBSWjIxdGFqZDVWbEZ2ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd4T1YxWnFUbnByTWs1WFZtaFBWR2hyVG5wQk5VMUVhek5QUkdoc1dsUk9iVmxYV1hoTmFrcHRDazlYVW1oTmFtc3hUVWRaTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhVTJkMVVqUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRU5raFNiSEJUV0hsYVUwUjVaREV5YldaNFdIUnpUbkZtUkhaTmFuWXpNRFkzU1NzNFdVNUtNR3BKVVVsb1FWQjNOd28zV21GclVVaFlNWFJ1ZDJRMVIzWkNXRzAzY0haM01uVXpNazFGYjFkMmNHdzJkSGd6Vm1oV1RVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxR1pVcDBkak15U0RaQlFrRkxTMmxsTm0xaGMweFdZa1JOUld0bmNVZDRVMGd5UnpCc2RscFpaMmt2V1RCRFlsb3JaRGxGTUZBM2VIVkZjWHBLVFU4S0wyZEplRUZRZWk5c2QxWXJNa1IzSzNBNVRtZEZVa1I0UVRKaE1XRlpWSE5LWmpScFpuaEdaRFJWWWxGVmIydERZM0p5TlVnMFExSXZWQ3M0WWxob0t3cHRjVUkyTUVFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1676421577,
          "logIndex": 13360252,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "e5ec7965ea98d70909788ee3faf122f9da2950f7",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4179423293",
      "sha": "e5ec7965ea98d70909788ee3faf122f9da2950f7"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

