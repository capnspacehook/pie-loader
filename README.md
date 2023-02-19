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
| `latest` | `sha256:fd8a52cd7045cbe506066a824ed1449c49ee171f89ba2a021496269f8b40390e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fd8a52cd7045cbe506066a824ed1449c49ee171f89ba2a021496269f8b40390e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:fd8a52cd7045cbe506066a824ed1449c49ee171f89ba2a021496269f8b40390e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "db28e2ce84359293ac9ecfc30de839cf3221f5b7",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCICNp44/TiuPH/S+AHdjI/JVJM5oQZtHVWOpGZePY9tFoAiEArfQtnzd0zcdGDaEorefrS0Bdssw22eswNuyy5aNPWsE=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI3YWIxNzg5MmFlMDMzODkwYjIzYzg4OTRmM2MwZWI0YmQ1ZDg1NmUyNjUyNDZhZTkyOGFmNzU3Y2IzOWFiNjMzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURGblhSbEQxdGM3RjFFMGpCRzJqb0tud3U5S2pZYzVYaE0yL0ZBdHZScUhRSWhBT2FZQTlqb0lJTnh3c1NweDJyWGx2emhnaVJtUmxPbE9LWnNZc3NLQk1yVCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjJla05EUVRCWFowRjNTVUpCWjBsVlZuQkNRalJzVERsTGNVUk1ZMlI0ZFZCaFdtMXBSeTl4WkZKQmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUlRWTlJFRjZUMVJOTTFkb1kwNU5hazEzVFdwRk5VMUVRVEJQVkUwelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZ3YUd4Qk1UUkVZMVV5WVVabFl6QkVTemxPWTA4eE4xUjNWbE0zWVUxc1EwVkNkMDBLTURZME9HdFFjSFJqZVV0cVVYbERZa1ZtWTNaMUszQlVUa2hSZWxOSVNIQkxURVJSTmtKbFRGWmpTV0pZWTFjd09UWlBRMEZ0VVhkblowcG5UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ2VVVVM0NraDZNMWRzTjNsMU1YQkZTRmRYUVdjM1VtbE5hMlkwZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0WmFrazBXbFJLYWxwVVp6Qk5lbFUxVFdwcmVsbFhUVFZhVjA1dFdYcE5kMXBIVlRSTmVteHFDbHBxVFhsTmFrWnRUbGRKTTAxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmIwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWkJValpCU0dkQlpHZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhYmtoTGNHWUtRVUZCUlVGM1FraE5SVlZEU1VkWGNETnhVbTFOT1hsb1kxRXdRMnRaWTJaeWMxQnBka3ByTkU1MWVqbFJhV1pOZVhadVYxTnJNVFZCYVVWQmMwSjNNUXBvT0ZWR1EzazRTV2xqWm5nd09GRlFOM281Y0hGUFFuQldhazU0TkdKTWFHeEdkVmxDVWtGM1EyZFpTVXR2V2tsNmFqQkZRWGROUkdGQlFYZGFVVWw0Q2tGT09EQkJkekJIU1RoT05rc3lNR05SWWtjeVRVeFhLME5GVFRWM1RYY3ZNMjFSVmxOallVaHNaMko1VXk5aE9ESkJNbXRhYmtwT1J6bGtTVTAzUnpjS1kzZEpkMEpMZFU1T2FsZG5jMmRDVEhFeU4wbHlaRVJNU0d0clduaElVWGR1YWtKcWNHWkZWVWw2TVRsemRuUnBjMmxvYlM5U1NqUmxWbEJETlhGRVpBbzRNRzF0Q2kwdExTMHRSVTVFSUVORlVsUkpSa2xEUVZSRkxTMHRMUzBLIn19fX0=",
          "integratedTime": 1676767195,
          "logIndex": 13652157,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "db28e2ce84359293ac9ecfc30de839cf3221f5b7",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4213754748",
      "sha": "db28e2ce84359293ac9ecfc30de839cf3221f5b7"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

