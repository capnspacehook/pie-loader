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
| `latest` | `sha256:159c8d053a273fc5127b611711d9ca9d4f61e9b3a9e9d890087969cf37f1faf7`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:159c8d053a273fc5127b611711d9ca9d4f61e9b3a9e9d890087969cf37f1faf7) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:159c8d053a273fc5127b611711d9ca9d4f61e9b3a9e9d890087969cf37f1faf7"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "6f8b43a4e7173c75abd4a1e224ebd2b741de82cf",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIFLxmnSccUTAE2bHlz5jLjeK2MsTzqhiTWeQkFQ1lPm9AiASJyjL3so+mDVSdPrgimvQORL5+GmqK4Qf59ox0NuuZQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4ZDhmOWJjNTU5NTcyOTk2MzY5NTQzOTQyOTlmNzU2MWM0OGQ3MmM2ZjlkZTU1MThlM2Q3M2VhMTI2NTVmMDg4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURnS01KWG1uMUtpUFpXSGZyVUVkR1lmamNqeTVCLzgvTjZuN0s2OWpiUDVnSWhBSWRGTHl0NmFwUzdRUEMzQXQzbXc3YytEbkVXdmFDTStaeHcvZzNyNHdIQiIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCWFowRjNTVUpCWjBsVlQxTkhUVmhLY1RBeFdFOUdiRll3Uml0emRXSktMMFIxVkV4cmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFVUVRWTlJFRjZUbXBSTlZkb1kwNU5hazEzVFZSQk5VMUVRVEJPYWxFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVU1TlVsNVVHaHVSV2R3U1hSWlRWVmllRkJ2Wmt4M2VIQlBSRzR6UlhGM1NsTkdTVVlLUkZrNE1WQTJhVEZPVEhaak1sZFFjMmtyY2tWQ1JXeGphelZxUlhZNGRFazNaRmhrZEZkTVJIRlhSVll3VTJSM1RXRlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZWVlZZMkNtdHRVRkZWZW1sbFRITnpRWFJsVWs5NE4yWldielV3ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpKYWFtaHBUa1JPYUU1SFZUTk5WR042V1hwak1WbFhTbXRPUjBWNFdsUkplVTVIVm1sYVJFcHBDazU2VVhoYVIxVTBUVzFPYlUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxYVkRsV05FUUtRVUZCUlVGM1FraE5SVlZEU1ZGRGRHMDNabFkxZVZSNmFGWjFiMXBwTDFOR2VsTklaelZRYVd0S0szbFFlVmRGVG5VdlFuRXlObFZ1UVVsblRUWkdlQXB4VTBsdU9VeDFWREpaV2s5alVHVnZjVGRNYlVSbGJHZFJiVkI0TVVaM2NVZzVhbWRrU0VsM1EyZFpTVXR2V2tsNmFqQkZRWGROUkZwM1FYZGFRVWwzQ21Vck1VWkZPR2gxVlRsTWVFTlFlRXhGVGtSb09IZG9Obk5aZFM5TVJpdE9OMnB3UjNOaFUyWXZRbmdyVG5neVltZFlTM2xpYW1ObGF6ZERUME12YVhrS1FXcENibk4zY2xSSVVHSlRRVFEzVVU0eGFUWXJWeXRyU0hGQ1ZteE9NR05yU0hndlVqVkhRVzFxYW5JMlUzSm1ha1ZPV2xveGRrbzFjMHhGVkhOa1R3b3hZMk05Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1673224633,
          "logIndex": 10760782,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "6f8b43a4e7173c75abd4a1e224ebd2b741de82cf",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3869710186",
      "sha": "6f8b43a4e7173c75abd4a1e224ebd2b741de82cf"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

