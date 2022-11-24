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
| `latest` | `sha256:f692fba75dafcff923cf03cd9af816d1477ce51c80370dc40f033b2a0b8b6406`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f692fba75dafcff923cf03cd9af816d1477ce51c80370dc40f033b2a0b8b6406) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:f692fba75dafcff923cf03cd9af816d1477ce51c80370dc40f033b2a0b8b6406"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "d386f9bcd758dfccc834aa2c5e36170bffeeb316",
      "1.3.6.1.4.1.57264.1.4": ".github/workflows/release.yaml",
      "1.3.6.1.4.1.57264.1.5": "capnspacehook/pie-loader",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/master",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIEqdrH5RsSYlmNF75W5D2FWglczi2FXwhwfIUx9dAc55AiEA9qvvrZJs7EzIxEsc2NfTcIoj3teHMHYuJZALcnOWU1M=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI2ODBlOWQ2MjVjNDczNGY4MDk5ZjIzMWQxZTY0MDdiZjA3NDg1MWI4ZjM5Njc0OTdhZmFjNjdiMWI1ODJkNDZkIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJRURZcDdXVWpud2J1Y0o3aStlNUZlTi9IVU85cmJWakJwZ1Z6bEkwNzl6dUFpRUEzc0Q5N0diYUo5ZnZrSGZ6MVRYRUM3U1lRRHkwOEw0Z0YxM0l1N2JGWkdnPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUjNSRU5EUVRCaFowRjNTVUpCWjBsVlFuTnJkSGhFU0RKRGJHeHBibnBpV2xaUFYwSm5XbTVxUlVkcmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RCTlJFRXdUV3BSTVZkb1kwNU5ha2w0VFZSSk1FMUVRVEZOYWxFeFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZrUm1oTWRWTkJNVXRxTVhKelJXY3lSME1yUTFCc05qaHRkVFIxYTNObFUwVkJZVVVLU3pVNWRWcE5Wa2RpYTBwM2JVY3ZZM0JWU2xoeVRuWldVVFZITldSU1ZHcG5NbE55TDBod2NFMXlOREZWTkZFMFdtRlBRMEZ0VlhkblowcG9UVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlUyT0d4c0NsVk1aRTF5VDBscU1scFJWVkJsYms5d1RUUTRZbkZaZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2FHTkhOWHBqUjBacVdsZG9kZ3BpTW5OMlkwZHNiRXhYZUhaWlYxSnNZMms0ZFZveWJEQmhTRlpwVEROa2RtTnRkRzFpUnprelkzazVlVnBYZUd4WldFNXNURzVzYUdKWGVFRmpiVlp0Q21ONU9XOWFWMFpyWTNrNWRGbFlUakJhV0VsM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEYUd0TmVtY3lXbXBzYVZreVVUTk9WR2hyV20xT2FsbDZaM3BPUjBab1RXMU5NVnBVVFRKTlZHTjNDbGx0V20xYVYxWnBUWHBGTWsxRGQwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlNHazFibUZZVW05a1YwbDJaREk1ZVdFeVduTmlNMlI2VEROS2JHSkhWbWdLWXpKVmRXVlhSblJpUkVGdFFtZHZja0puUlVWQldVOHZUVUZGUmtKQ2FHcFpXRUoxWXpOQ2FGa3lWbTlpTWpseVRETkNjRnBUTVhOaU1rWnJXbGhKZHdwSWQxbExTM2RaUWtKQlIwUjJla0ZDUW1kUlVtTnRWbTFqZVRsdldsZEdhMk41T1hSWldFNHdXbGhKZDJkWmMwZERhWE5IUVZGUlFqRnVhME5DUVVsRkNtWlJVamRCU0d0QlpIZEVaRkJVUW5GNGMyTlNUVzFOV2tob2VWcGFlbU5EYjJ0d1pYVk9ORGh5Wml0SWFXNUxRVXg1Ym5WcVowRkJRVmxUYmtaclZtUUtRVUZCUlVGM1FrbE5SVmxEU1ZGRGJrTkVOV1JOY1dSamMxZFNlRkpRT0RKa2VtUXJVR1Z5Tkd4Nk1qWmpkMVZRWW5CcU1tTkNaa0YyVVVsb1FVOUtWd3AxTmpKclZreENhWGx4WlM5SmVqWjZOR3RhVmpCVldtVlRNVTk1UVVWTFYyRlVVRTkwU0dwelRVRnZSME5EY1VkVFRUUTVRa0ZOUkVFeVowRk5SMVZEQ2sxRlUySXpOVmxJV0VwaVltVlpWazA1Y3pCaGFDOUdOVkZTUzB0c1p6RXpZVlZVVlZodFVXSlBNbVUxTVdsVVVEUndjalJLVDJ4MFltUlZlVU5wUjJzS1drRkplRUZMWW1sU1ZVdE1WQ3RHVTJ0U2QwWkpTVTVpZG5ad1oxWTRPRzFFWW13MFVGcFdRVTl3YmxkUWNHTkNlQ3RQTVVoT2FrOUlaVzFwZGxVMlJncERhak5wVjNjOVBRb3RMUzB0TFVWT1JDQkRSVkpVU1VaSlEwRlVSUzB0TFMwdENnPT0ifX19fQ==",
          "integratedTime": 1669250584,
          "logIndex": 7724156,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/capnspacehook/pie-loader/.github/workflows/release.yaml@refs/heads/master",
      "githubWorkflowName": ".github/workflows/release.yaml",
      "githubWorkflowRef": "refs/heads/master",
      "githubWorkflowRepository": "capnspacehook/pie-loader",
      "githubWorkflowSha": "d386f9bcd758dfccc834aa2c5e36170bffeeb316",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3536743308",
      "sha": "d386f9bcd758dfccc834aa2c5e36170bffeeb316"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

