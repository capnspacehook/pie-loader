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
| `latest` | `sha256:ddcda56477563674283c09e6602efbaae96dbeb655cdfcc22eb643f7bf705a7b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ddcda56477563674283c09e6602efbaae96dbeb655cdfcc22eb643f7bf705a7b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:ddcda56477563674283c09e6602efbaae96dbeb655cdfcc22eb643f7bf705a7b"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "1c23797ade94a78c105821167d72bbe5f1a0aa90",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQDFSJE10M5wc51r4TKLdxkaA4wnK3OKWg/bc+abptAFuQIge7ZfzXfasPdmm/3FId7Ngy8RYQj+gqu1t0FMJ5y89Yg=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4ZDg3MjI1ZDZiNTk4NDZhOGRhNDdhYTAzZjQ0ZWQ1ZDRmNjc3ODYxODJlM2NkODUyOGMzMzk2YjdjOGI2MzIxIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUNSQTBUSFdCTFhhdzdyYVFuZlc3SWV5Z2cvejdGMFk5M2xIelhsWU9PYkRBSWdCZy9ab2ZCc0tiRkwyRnYxQkJDN1BGaUxlb2sxY3J4eWxNUk5TZ1B3T3I0PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlRFaHRZa1JsYkhsbVZGbGlZbFF5UVhOcFZGZ3dWSEo1UkcxTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVRCTlJFRXdUMVJKZUZkb1kwNU5ha2w0VFZSQk1FMUVRVEZQVkVsNFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZqUWs1TVdGRldaRzQzWjJWU1lUSnhUbE4xUnpZMlV6UlZSekJ3UlZGSVNIb3pkR0lLTmk4eE9HMU5la2RYZFRnNWJGRTVXVzlGZHl0NlZYbHhibUZEZUZsdU0xRlVPRTVVZUhadlUzUktXRlFyTVZGNk1qWlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV3YTJkb0NqRjNXVkpQZGprM1RVTlNOa2RXU210aldrZE5TbkpCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoWmVrbDZUbnByTTFsWFVteFBWRkpvVG5wb2FrMVVRVEZQUkVsNFRWUlpNMXBFWTNsWmJVcHNDazVYV1hoWlZFSm9XVlJyZDAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxTUVVoVFJsQUtRVUZCUlVGM1FrZE5SVkZEU1VKRE1rcEpVV3RQVDA1SlNYbDFkM0ZDWjNseGMyMXdTVXBIYWpOblFXNXRkV2x6YmpadU9GZDJPUzlCYVVGVVRHUlFTZ28zYVZoaVpEQlhTbW93YVZwemVYTnpjM2xpYWk5UU5HdFZTaTlrVDI5T09Ib3pPRnB6ZWtGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha0p4Q25GUmJ6WXJjRFUyU0hKMlkwRXpTbVJQYWxwdlMydEVRM0ZYVDNwb2REZG9RM1pqVmpJd1FWWXhiSEoxU21SVlYwdElhMEp2Y0VaMlRqa3JUMnR5YjBNS1RWRkVlVWhqZWtSdGQzSkRhR2hTTTNnd09IRnNZM1JPYm5neFEzaERXVXBaYUZkdGJYQmtUazlMYjNwQ1RYQjZZMmxHVm5rMEwyMXZkRmszUjA1dmJBb3JOemc5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667522994,
          "logIndex": 6457390,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "1c23797ade94a78c105821167d72bbe5f1a0aa90",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3390405516",
      "sha": "1c23797ade94a78c105821167d72bbe5f1a0aa90"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

