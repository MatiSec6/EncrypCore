# EncrypCore

![EncrypCore terminal preview](docs/preview.png)

EncrypCore is a terminal cryptography toolkit. It encrypts files and text, hashes passwords, signs files, and provides JWT, TOTP, certificates and a few learning tools.

> **Use it carefully.** Losing a password or key means losing the data. Read [docs/SECURITY.md](docs/SECURITY.md) before relying on it.

## Windows: quick start

**Option A: no Python needed (recommended)**

1. Open the **Releases** page of this repository and download `EncrypCore-windows.zip`.
2. Extract it and open PowerShell in that folder.
3. Run `.\encrypcore.exe --help`

**Option B: from the source code (Python 3.10 or newer)**

1. Extract the project folder.
2. Double-click **install.bat** and wait for "Installation complete".
3. Open PowerShell in the project folder and run `.\run.bat --help`

## Examples

```powershell
.\run.bat gen-key                         # random AES key and password
.\run.bat aes enc "my secret note"        # asks for a password
.\run.bat file enc report.pdf             # creates report.pdf.locked
.\run.bat pass-hash                       # hashes a password for storage (Argon2id)
.\run.bat gen-cert --domain localhost     # self-signed certificate for local testing
```

Replace `.\run.bat` with `.\encrypcore.exe` if you use the exe version.

## Commands

| Command | What it does | Asks for a password or secret |
| --- | --- | --- |
| `aes enc` / `aes dec` | Encrypt or decrypt text | Yes |
| `file enc` / `file dec` | Encrypt or decrypt a file | Yes |
| `pass-hash` / `pass-verify` | Hash a password, or check it against a hash | Yes |
| `ecc-keys`, `ecc-sign`, `ecc-verify` | Create keys, sign text, verify signatures | No |
| `sign-file`, `verify-file` | Sign a file, or check that it was not changed | No |
| `jwt-gen` / `jwt-verify` | Create or verify a JSON Web Token | Yes |
| `totp-secret`, `totp`, `totp-verify` | One-time codes for two-factor login | Yes |
| `gen-cert` | Self-signed certificate for local development | No |
| `shred` | Overwrite and delete a file (best effort) | No |
| `gen-wallet` | Educational wallet key generation (not for real funds) | No |
| `classic`, `crack`, `auto`, `stego`, `gen-key` | Learning tools and helpers | No |

Full details: [docs/USAGE.md](docs/USAGE.md). Testing: [docs/TESTING.md](docs/TESTING.md).

## Important

- Passwords and secrets are always typed in hidden input. They are never passed on the command line.
- Self-signed certificates are for local development only.
- The classic ciphers, the dictionary checker and the steganography tool are for learning. They do not protect anything.
- Do not use the wallet keys for real money.

## License and author

MIT License. See [LICENSE](LICENSE).
Author: MatiSec6 (matisec.dev@gmail.com)
