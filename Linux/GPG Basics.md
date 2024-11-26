# Creating GPG
To create an encryption key, use `gpg --full-gen-key`. This will first let you select the kind of key that you want, such as RSA, DSA, ECC, etc. This will then ask you about the expiration, `Real Name`, `Email`, and `Comment`. Finally, this will ask for an optional passphrase that if you set it, you won't be able to access it unless you supply the passphrase.

# Encrypting files
To encrypt a file, you use `gpg --encrypt -r <recipient_email> <file>`. This generates a `*.gpg*` file that is garbled since this is encrypted.

You can also use the `--armor` option for a more presentable output. This is only viable for text encryption.
# Decrypting files
To decrypt files, you use `gpg --decrypt <file> --output <file>`. This will then ask for the passphrase if set. 

# Signing and verifying
## Messages
You can pipe a message into the following command:
`gpg --clearsign -u <email>`

To verify the message, simply use `gpg --verify <file>`

## Encrypt and sign at the same time
To encrypt and sign a message into a single file, you can use the following:
`gpg --armor --sign --recipient <fingerprint> --encrypt secret`

## Files
To sign a file using gpg, you usually create a separate signature file. In this case, you use `gpg --detach-sign -u <email> <file>`. This creates a separate signature file `*.sig`. To verify using the signature, you can use `gpg --verify <signature_file> <file>`.
## Note on file verification
A signed file remains valid as long as it has not been modified since the last time the file was signed.

---
Related:
`man gpg`
[GPG: A comfy guide](https://www.youtube.com/watch?v=eLKOIjNFwVs)


#linux #gpg #encryption