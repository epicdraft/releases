# EpicDraft — public installer downloads

This repository holds **installer binaries only**. There is no source code here.
EpicDraft's source lives in a private repository.

## Why it exists

The Microsoft Store submission API does not accept a file upload for EXE/MSI
apps. A submission carries a `packageUrl`, and Microsoft fetches that binary
itself — anonymously, both at certification and when a customer installs the
app. Release assets on a private repository return 404 without a token, so they
cannot be used for this.

Each release here mirrors the Microsoft Store MSI for one version, at a stable,
versioned URL:

```
https://github.com/epicdraft/releases/download/epicdraft-v<version>/EpicDraft_<version>_x64_<locale>_store.msi
```

Uploads are automated by the `Windows Submission` workflow in the main
repository. The binary behind a submitted URL must never change, so each version
gets its own release and is published once.

## Verifying a download

Installers are signed by **EpicDraft, Co.** through Azure Trusted Signing. On
Windows, check before installing:

```powershell
Get-AuthenticodeSignature .\EpicDraft_<version>_x64_en-US_store.msi
```

`Status` should read `Valid`, with the signer showing `EpicDraft, Co.`.

## Looking for the normal download?

Most people want <https://epicdraft.com>, or the Microsoft Store listing. The
files here are the same builds, published for the Store's benefit rather than
for direct download.
