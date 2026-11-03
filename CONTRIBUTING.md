# Contributing to EncrypCore

Thank you for your interest in improving EncrypCore. This guide explains how to set up the project, run the checks and send a change.

## Ground rules

- Keep changes focused. One pull request should solve one problem.
- Do not change behaviour that is not related to your change.
- Never commit keys, passwords, certificates, `.locked` files or signatures, even as examples. The `.gitignore` already excludes common patterns, but check your changes before committing.
- Security issues must be reported privately. See [SECURITY.md](SECURITY.md).

## Setting up

Windows (PowerShell), from the project folder:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -e ".[all,dev]"
```

## Running the checks

Before you open a pull request, run all of these:

```powershell
ruff check src tests
python -m unittest discover -s tests -t . -v
python scripts\smoke_test.py
```

- `ruff` checks style and common mistakes.
- The unit tests cover every core module and the command-line interface.
- The smoke test runs the commands that do not need a typed password.

Tests for optional features are skipped with a message when their package is not installed. Install `[all]` to run all of them.

## Code guidelines

- Use Python 3.10 or newer. Do not use features from later versions.
- Put cryptographic code in `src/encrypcore/core/`. Use the standard `cryptography` library and the maintained packages already listed. Do not write your own cryptographic primitives.
- Passwords, secrets and keys must be read with hidden input, never passed as command-line arguments.
- Errors shown to the user must be clear and must not reveal secret data.
- Add a unit test for every new behaviour, including the failure cases.
- Keep user-visible text short and in English. Update `README.md` or the files in `docs/` when a command or option changes.

## Commit and pull request

1. Create a branch from the latest main branch.
2. Make your change and add tests.
3. Run the checks above.
4. Describe what changed and why in the pull request. Mention any command or output that changed.

## Release process

Releases are made by the maintainer. A version tag such as `v1.0.1` triggers the Windows build and publishes the executable and its checksum. Do not change the version number in a pull request unless the maintainer asks you to.

## Questions

Open an issue for questions and ideas. For security issues, use the private route in [SECURITY.md](SECURITY.md).
