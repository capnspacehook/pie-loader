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
| `latest` | `sha256:b3636ce43f018ac281adaa6a448eab76aa2e15d5b552702d74ef4d2cf7cf2798`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:b3636ce43f018ac281adaa6a448eab76aa2e15d5b552702d74ef4d2cf7cf2798) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:b3636ce43f018ac281adaa6a448eab76aa2e15d5b552702d74ef4d2cf7cf2798"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "274349ee0bcdf277c8912642d7fa943ada295512",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCICM1BG03HKHJtUuhybD1ZYxfbCozMlnlwqrkvr9JoYW+AiEAoa79g7b3nOVgSdR1XlBslPlj9aQqz4fOPJIWjASBVYk=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJlMDNmMTg3MDk3MjE1MGRjZGI0MjZkNGFiYjExNDgzNDhhNWY4OWRlMTlhYzYxODE5ZTAxNzlkZDZjYTY0NWJmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURkbWRoVmJpR2V5dUhYMWEvczR3dDdpVEFLWTRlRkVpMXJVbUJ6MXNpaWVRSWhBSitHK1pkd2FHUHhOWWNkaENYL0VWdmdFSWxKOGM3eDRRZ3EyS09LcHJZMSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNWRU5EUVRCaFowRjNTVUpCWjBsVlRtaFFhVk00YzBwcFdrb3dSbk54YzB3MGQyVXpaMlZaU2lzNGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDFxU1hoTlJFRXdUV3BCTWxkb1kwNU5hazEzVFdwSmVFMUVRVEZOYWtFeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVYxVERZeU1rWmxOeXRYUVVwaFYyVk5SM1YxUzBWclVHSlVhM1ZPZWtGTlkwTmxPSG9LYlRkMVpraEthRWROVkZsQ2RHTkJia1F6UW5kRWMzZHZVMkZIZHpsVVUwbExVbmhoU0U5dE1HRXJWRGM0T0ZWdlREWlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYyV0VFdkNsSXpXRnBxYjFkbE1XSkJlRFZ1TkRSelNEQnJUeTl6ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNsT2VsRjZUa1JzYkZwVVFtbFpNbEp0VFdwak0xbDZaelZOVkVreVRrUkthMDR5V21oUFZGRjZDbGxYVW1oTmFtc3hUbFJGZVUxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxhZUdFMmJrSUtRVUZCUlVGM1FrbE5SVmxEU1ZGRU9FSjVWR1UyYUhacGRHbG9SbE5sU2k4clFqUmhNeTl1YVhaUGNqWjRUMWx2ZG5KamVVd3dVRTFTZDBsb1FVcEVVQXB1T0RKalMyRlFlVGxxWWxoRFUySlRibU5GYW5kMFRUSnhWbUZpZDNweVMwUkxPRTFvU2xKUlRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeWEwRk5SMWxEQ2sxUlEwbG9kV3R3U2pSS05XNXdTV1p4SzNFMU9FUmpVemhoZUZsVFNUSk9Sa1ZZTDNvd1ZUQldRVlZ1YlRkNVEyMXZhMFJITTNjcldrMW5SMUo0Tms4S0wwWlZRMDFSUTNKd1NpdHZiVmRqY0VWelMxUjZkR0ZDUlhoWVJFRTBUMDFVT1RSTVIySnBTMVpKTWxrcmNVaHZWemRLVFV3cmVtdEZTR00wYlRSSU13cGlkVE5rU1N0elBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1676940147,
          "logIndex": 13795509,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "274349ee0bcdf277c8912642d7fa943ada295512",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "4228153210",
      "sha": "274349ee0bcdf277c8912642d7fa943ada295512"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

