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
| `latest` | `sha256:e79ae1541842e0108e49f7561643627e379c0f1cbcd28307acac24774e3b9fc5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:e79ae1541842e0108e49f7561643627e379c0f1cbcd28307acac24774e3b9fc5) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:e79ae1541842e0108e49f7561643627e379c0f1cbcd28307acac24774e3b9fc5"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "372d49cc7d273b3a6b322562c008aa70d7ec838e",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCWl6pwkH3TnmohSC5P5tXUAB8ork+C2iCBBl3PPRyIYQIhANfgCgkntuzuaMMaiXPkdmb0RabuTqbfeJwEu2EInzfK",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIzZTFjOTFkZGRlZWFjNDAxYmFhZjc1N2E2MjFkMTJjZmRmYzlmMGVjNjVkMTY0Y2MzNGNkNGY4Yzg5YTI2MTM5In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQk9sTkRyL3NKQWt6VUE2UjRKc05sdXEwb0VKeURvMklWTlIzb2swK2RyQ0FpQW5BdFZWUlpwZzFrLzV0TC9GdHVyaENqZSt1aTQzRmE4WmkrK25iNStvZ3c9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlFXWkRZVk5NZWtOb1VIZHNWbGxtV2tZd2IzcDRjVFV5U2toM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVRCTlJFRjZUbXBCZWxkb1kwNU5hazEzVFdwQk1FMUVRVEJPYWtGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV6ZDFkeVpVNUpiWG8yUkUxYVNYSTNhVkV6Uld4TU1VRjNlakZGZUROa0wyeDRTRzBLVmpkV2JUWXJPSEF5VTBvMVN6SmFhWEJrV0ZWaWJHVnVVbWRDZEVObWRtRk9WbE01VkZONlFYQjZXSEpwUm5WalVqWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZUZFhocENrMW9XbVJEWm1OYVUxTmxUVGh4U0c1Q1ZUQlFXV2RGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNwT2VrcHJUa1JzYWxsNlpHdE5hbU42V1dwT2FFNXRTWHBOYWtreFRtcEthazFFUVRSWlYwVXpDazFIVVROYVYwMDBUWHBvYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaV2pKblNHMEtRVUZCUlVGM1FraE5SVlZEU1ZGRFRVdDNPRUpyVEZoT1JEbGFLMDQwWlZsS1J6Sk1ZM0Z3TkdaQ1RtRnpVV0pQUkU5dFQwVnNjQzlGWjBsblMxRnhiUXBZVjFaVGJIb3lielpCUWpScVVWWnpLemRGTW1SRFYwTkJaeXMxTms4clpFcGxablEwUkVGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGTFIwWnFWRGRETjFoS1dtb3JVV2N3VlN0MVJGWjJOblJITDFaR2QyZzBlRlprSzBSc1dFOVRZbTl4TVhVeFlYQkxNMGQ2WXpObmRtaGhNbmxpV2swS1NuZEpkMUJTU0VKa1FWQmxibTFUV1dWaVkxaGhPV2ROVURCalFqVlJaMUp1VlZoRlZISlZiVWMwZFVkd1VqUkZSalkyYWpWUlNXMHdUemRNYjBkSlp3cFlkSEY0Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1675470989,
          "logIndex": 12578567,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "372d49cc7d273b3a6b322562c008aa70d7ec838e",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4089039559",
      "sha": "372d49cc7d273b3a6b322562c008aa70d7ec838e"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

