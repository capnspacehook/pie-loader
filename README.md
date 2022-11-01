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
| `latest` | `sha256:a296226747e289bbba1e092c2c7e5c51ced2551fb991b48cecc2085b94459db2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a296226747e289bbba1e092c2c7e5c51ced2551fb991b48cecc2085b94459db2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:a296226747e289bbba1e092c2c7e5c51ced2551fb991b48cecc2085b94459db2"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "4ac0525a1388d47b371c1d0d0f9c1742a999f524",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQC7rDfxSMj4dI3hlwUaoxjAZMgeu9aH8q9AK2ib3fNSOQIhANYo5FVXETE/Xo+e3lz0YH1lR2js+ZwHOL5rajV7uA8A",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4NjM0Njc0YTYwODQ2YTUwMTdkZjFhZWFlNWVlMGY5OGI5YjFlNmUzNzQ0NzFhYTc4NmRlZDAwNDE4OGVhYWI4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQmRhaVEyVy8yT3VmVlZoSU1xK2s5Zjhxbk1MRW5HbGxnU1BNT2tVb1ZoMEFpRUE0Z2NFNUhYUjVKRmlQNlE3NVJIOWtHczlRblZBSEhNYmFTQzZXS3k3aC9zPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJha05EUVRCVFowRjNTVUpCWjBsVlNIUkRka0pVZFhkcVZYTkdSMlpTYVVwUFpFMU9iMkZxTW1sSmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUVhoTlJFRXhUbnBKZVZkb1kwNU5ha2w0VFZSQmVFMUVSWGRPZWtsNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYxTVZwUmFEVnFWVVZNWlVveVJVZEhNVmxDYUVacVZUaFlhRGQxTVRodVJHOXVObFlLWWpCMkx6ZGxZbmxzTjBabFJEVTJTVnB6UkVvemNESnpVMGwxY1dwalExVnhPVW8xUVhsWmJYRkliRTkxUldGcEwyRlBRMEZ0VFhkblowcG1UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ2ZWxBMUNsQXhWQ3RvVFdJelVHMUZWV2h3YldKRloxRXZVMWRGZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpCWlYwMTNUbFJKTVZsVVJYcFBSR2hyVGtSa2FVMTZZM2haZWtaclRVZFJkMXBxYkdwTlZHTXdDazF0UlRWUFZHeHRUbFJKTUUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmEwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtVjNValZCU0dOQlpGRkVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxSZDNOWFRsTUtRVUZCUlVGM1FrZE5SVkZEU1VkeWJXazNUM2R5U0VVMlJHWnRhWGMzVDFKM1ozcEpUazFyUkROUGMxZDVVMFJGWXpkUmFWSkJibEJCYVVGVVpreENkZ3BQV25CMlVtTjViMU5qWnpSb1oxRldNV05ZV0dKaVdEZDFNMmMzWlVOaVJXUlhiRzlPUkVGTFFtZG5jV2hyYWs5UVVWRkVRWGRPYjBGRVFteEJha1ZCQ2l0aWRFdFJORVZLWkhCbVVtMDBVMmQ0VG00NGEySTVVMFEzVWxveUswUlZTbk42TUhsSll5OU9ORW94Y0dwdFZHeE1NRXg0VEV0eU0yeE1XWHBZYm5vS1FXcEJUV2tyVFRsTkszRnNNMjFaUkZodVJsSk5NQ3RJZEdWMU4wVjZRbGRJTjIxaVdFNUplbTh3WmtWak1YRk5MMUkwWTAweE9FMHhjVXA2Wmtwa1NBcE5NVzg5Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1667264266,
          "logIndex": 6260300,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "4ac0525a1388d47b371c1d0d0f9c1742a999f524",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3365917227",
      "sha": "4ac0525a1388d47b371c1d0d0f9c1742a999f524"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

