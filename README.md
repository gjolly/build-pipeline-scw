# Ubuntu build pipeline

The main show happens here: https://github.com/gjolly/build-pipeline/actions/workflows/build-image.yaml

This repository contains the configuration for an image build pipeline of Ubuntu hosted on Github Actions.

Images produced here are unofficial and not supported by Canonical, however they only contain official packages from Ubuntu.

# Last built images

![Today's build results](https://github.com/gjolly/build-pipeline/actions/workflows/build-all.yaml/badge.svg)

<table>
    <thead>
        <tr>
            <th>Version</th>
            <th>Architecture</th>
            <th>URL</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>Ubuntu 22.04 LTS - Jammy Jellyfish</td>
            <td rowspan=1>amd64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/jammy-amd64.img">jammy-amd64.img</a></td>
        </tr>
        <tr>
            <td rowspan=1>arm64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/jammy-arm64.img">jammy-amd64.img</a></td>
        </tr>
        <tr>
            <td rowspan=2>Ubuntu 24.04 LTS - Noble Numbat</td>
            <td rowspan=1>amd64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/noble-amd64.img">noble-amd64.img</a></td>
        </tr>
        <tr>
            <td rowspan=1>arm64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/noble-arm64.img">noble-arm64.img</a></td>
        </tr>
        <tr>
            <td rowspan=2>Ubuntu 24.10 - Oracular Oriole</td>
            <td rowspan=1>amd64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/oracular-amd64.img">oracular-amd64.img</a></td>
        </tr>
        <tr>
            <td rowspan=1>arm64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/oracular-arm64.img">oracular-arm64.img</a></td>
        </tr>
        <tr>
            <td rowspan=2>Ubuntu 25.04 - Plucky Puffin</td>
            <td rowspan=1>amd64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/plucky-amd64.img">plucky-amd64.img</a></td>
        </tr>
        <tr>
            <td rowspan=1>arm64</td>
            <td rowspan=1><a href="https://objectstorage.eu-marseille-1.oraclecloud.com/p/890K8izdHm5rICdcJzJHQBA19nzx2zHoKmR4E2y2ejGiY_kCRzyh4a1s5yMTyLfJ/n/axd1qa3z3pet/b/live-images/o/plucky-arm64.img">plucky-arm64.img</a></td>
        </tr>
    </tbody>
</table>

# Attestation - How can you verify that these image were built on Github?

All the artifacts built here are attested to establish their provenance. You can use the Github CLI to verify that a given artifact that you download was indeed built here. For example, for the Ubuntu 22.04 LTS "Noble Numbat" AMD64 image:

```bash
gh attestation verify noble-amd64.img -o gjolly
```

And you should see something like this:

```
Loaded digest sha256:aa14d0671d23dc7ee74b8950dc6dc0224209a61d7b415e40f4c1b234398d5f05 for file://noble-amd64.img
Loaded 1 attestation from GitHub API

The following policy criteria will be enforced:
- Predicate type must match:................ https://slsa.dev/provenance/v1
- Source Repository Owner URI must match:... https://github.com/gjolly
- Subject Alternative Name must match regex: (?i)^https://github.com/gjolly/
- OIDC Issuer must match:................... https://token.actions.githubusercontent.com

✓ Verification succeeded!

The following 1 attestation matched the policy criteria

- Attestation #1
  - Build repo:..... gjolly/build-pipeline
  - Build workflow:. .github/workflows/build-image.yaml@refs/heads/main
  - Signer repo:.... gjolly/build-pipeline
  - Signer workflow: .github/workflows/build-image.yaml@refs/heads/main
```
