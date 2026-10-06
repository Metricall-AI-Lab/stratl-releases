# Stratl verifier

`stratl` checks a Stratl evidence bundle entirely offline: the record hash, the ES256 signature
against the workspace's published public key, the hash chain, the Merkle checkpoint and the
RFC 3161 timestamp. It needs no account, makes no network calls and does not trust Stratl.

This repository holds the released binaries only. Each release carries six archives (macOS,
Linux and Windows, Intel and ARM), a checksums file and a software bill of materials for every
archive.

## Install

macOS, with Homebrew:

```bash
brew install metricall-ai-lab/tap/stratl
```

Everything else: download the archive for your platform and `stratl__checksums.txt`
from the [latest release](https://github.com/Metricall-AI-Lab/stratl-releases/releases/latest),
check it, unpack it.

```bash
shasum -a 256 --ignore-missing -c stratl__checksums.txt
tar xzf stratl__linux_amd64.tar.gz      # Windows: unzip the .zip
./stratl --version
```

## Use

```bash
stratl verify DEC-….stratl.zip      # a bundle exported from the portal or the API
stratl verify ./DEC-….stratl/        # the same bundle, unpacked
stratl inspect record.json           # the canonical form and hash of one record
```

Exit status is 0 only when every check that could run passed.

## How it is built

The verifier is written in Go and released with goreleaser from the Stratl platform repository,
which is private during early access. Record format: [docs.stratl.ai](https://docs.stratl.ai/developers/build/record-format/).
Verifier reference: [docs.stratl.ai/developers/build/verifier](https://docs.stratl.ai/developers/build/verifier/).

Licence: Apache-2.0.
