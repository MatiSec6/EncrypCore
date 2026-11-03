# Changelog

## 1.0.0

Initial public release.

- AES (Fernet, PBKDF2-HMAC-SHA256 key derivation) for text and files, with atomic writes.
- Argon2 and bcrypt password hashing (optional dependencies).
- ECC (SECP256R1) key generation, text signing and file signing.
- JWT (HS256) generation and verification (optional dependency).
- TOTP generation and verification (optional dependency).
- Self-signed TLS certificate generation for local development.
- Secure file shredder with confirmation (best-effort; see README).
- BIP39 / BIP32 / BIP44 wallet key generation for education (optional dependency).
- Educational tools: ROT13, Caesar cipher, Base64/Hex auto-decoder, dictionary hash checker, zero-width text steganography.
