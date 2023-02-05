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
| `latest` | `sha256:2782f145f71d6ddbf8aa5e13039d932927c18b141deb9fb81aa9c670b46f5679`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2782f145f71d6ddbf8aa5e13039d932927c18b141deb9fb81aa9c670b46f5679) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:2782f145f71d6ddbf8aa5e13039d932927c18b141deb9fb81aa9c670b46f5679"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "cd70fb4030970de409ae1a7cbf4ee5ce7358bade",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIHOWREyUNDOnvY14PqHz7u6gDF42Lj5/Rv5mCWgac8WwAiEAozbf/esRBOHUy86roR8bPvLk/a9naydmkCXleIg5UNo=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhODVhZmY3N2Q1ZGI2YTA1YjY0YTVmODNhZTUxNDU5Y2QwNjA3YjFlOTZlZjU5OWZiOTU1YzZkNDE4NmQxZjc0In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRFV4SVh1dVRiOERzN0Y5QVdSTVM4ZmQ5NncrN2haeHR4ckxGZEF3V0JtUEFpQXh5ckhvSG9uNHYwcFo4UXhMay9UMFN3YndBT0p4cGszK1RWcWpPMTFOM1E9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlJYQmxMemw0Um1KSE16RjJWVEFyUVc0eU4xWXliRGd4WjJSWmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxUVRGTlJFRXdUVlJSZWxkb1kwNU5hazEzVFdwQk1VMUVRVEZOVkZGNlYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZIYjNWUVMwNXJhSFZwV0haNlFrZDBNVlF4YW5oYU1GUTJLMnBoVWxFdlpUUjVZVGtLZDJKaVZreHFUbXBJVW5JeVptZEVaRmcwZW1aUFNYbFpLM041VldkalRWVnllbXg0VVhOTWRGbDJRMnRXVURWVU1YRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZOYlRVMkNqVlRObHBTT1hJck0zRlVZM293TmxFelpFdFNPWE5OZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUdwYVJHTjNXbTFKTUUxRVRYZFBWR04zV2tkVk1FMUViR2hhVkVab1RqSk9hVnBxVW14YVZGWnFDbHBVWTNwT1ZHaHBXVmRTYkUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxaWmtKYVJHNEtRVUZCUlVGM1FrbE5SVmxEU1ZGRFlraHRRWE4wWm5WeFZ6TmFTVWw0YTJoTUwzRkhjMjU2WXpGWGJXZDNhV1J1V2xVeVZHcGlXV0pwUVVsb1FVOVlXZ3BCYUV4NWVqaEZNRmsxY0VWVmVtbG5MM1pUVVRSQlRHcE9RMHRyTTBOMVF6aDJiR05aTTA1alRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxUlEwdHZUV0ZLYzNoR05HOUphbWRyT1VkaFZUZENUMFpRV21GTFJsaEtSRk0yZFd0TFRIWlVkMGt5WWtGSVV5dG9XRkUwUTA1eVZWZFBabEpPT0hnS2NuWXdRMDFETjNCSldGUTRSVTlOTURsSk1HVk5kVkp2YVZrNFlscFJRekY2YkRSd1FYVXhURXB3VEZSRmQycFhNeXRIYVhFMU5YbHlXRXdyVUdVMGR3cGxlbnBtVkZFOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1675557723,
          "logIndex": 12642268,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "cd70fb4030970de409ae1a7cbf4ee5ce7358bade",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4094164278",
      "sha": "cd70fb4030970de409ae1a7cbf4ee5ce7358bade"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

