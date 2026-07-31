# GnuPG (GPG) Encryption in Linux

---

# What is GnuPG?

GnuPG (GPG) is a tool used to:
- Encrypt files
- Decrypt files
- Manage cryptographic keys

It supports:
- Symmetric encryption
- Asymmetric encryption

---

# 1. Symmetric Encryption

In symmetric encryption, the same password is used for:
- Encrypting the file
- Decrypting the file

## Encrypt a file

```bash
gpg -c file.txt
```

This creates an encrypted file:
```text
file.txt.gpg
```

## Decrypt a file

```bash
gpg file.txt.gpg
```

You will be asked for the same password used during encryption.

---

# 2. Asymmetric Encryption (Public Key Encryption)

Asymmetric encryption uses:
- Public key (to encrypt)
- Private key (to decrypt)

---

# Step 1 — Generate Key Pair

```bash
gpg --gen-key
```

This creates:
- Public key
- Private key

---

# Step 2 — Export Public Key

```bash
gpg --export -a "username" > publickey.asc
```

This creates a shareable public key file.

---

# Step 3 — Share Public Key

Send the public key file to another user securely.

Example:
- gbg1 shares `publickey.asc` with gbg2

---

# Step 4 — Import Public Key

On the receiving machine:

```bash
gpg --import publickey.asc
```

This adds the sender's public key to the key database.

---

# Step 5 — Encrypt a File Using Public Key

```bash
gpg -r gbg1 -e file.txt
```

Meaning:
- `-r` → recipient
- `-e` → encrypt

Output:
```text
file.txt.gpg
```

Only the owner of the matching private key can decrypt it.

---

# Step 6 — Transfer Encrypted File

Move the encrypted file to the recipient:

```bash
cp file.txt.gpg /home/gbg1/
```

---

# Step 7 — Decrypt File (Receiver Side)

```bash
gpg file.txt.gpg
```

The system will:
- Detect the private key
- Ask for the passphrase
- Decrypt the file

---

# Summary of Flow

## Symmetric Encryption
- One key (password)
- Same key encrypts and decrypts

## Asymmetric Encryption
- Public key → encrypt
- Private key → decrypt

---

# 🧠 Summary

GPG is a powerful encryption tool used in Linux for secure communication and file protection. Symmetric encryption is simpler but less secure for sharing, while asymmetric encryption is widely used in real-world systems for secure key exchange and data protection.

