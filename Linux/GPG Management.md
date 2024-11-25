The basics cover key creation, encrypting, decrypting, signing and verifying files. This section covers key management in general.

# Checking for existing keys
Run the following command to see if you already have keys installed:
`gpg --list-keys`

# Editing your keys
You can edit your keys using `gpg --edit-key <email>`. Then you can select the key you want to edit using `key <number>`. Here you can reset your key expiration dates by typing in `expire`, then the number of days, weeks, months or year to ensure your keys don't expire.

# Changing the passphrase
Change the passphrase of your GPG keys using `gpg --passwd <email>`.

# Revocation certificates
Since GPG 2.1, revocation certificates have already been created. By default, they would be stored in `~/.gnupg/openpgp-revocs.d` (at least on my machine), usually looks like `<cert_id>.rev`. Importing this revocation certificate using `gpg --import <cert_rev>.rev` will revoke whatever cert this is associated with.

# Backup and Restore
Backing up and restoring GPG keys is as easy as backing up the following `$HOME/.gnupg` folder.
Sure there are other ways to export secret keys, such as the following:
`gpg --export-secret-keys --output <export_file>.gpg --armor <email>`, but it's usually easier to just export the whole `$HOME/.gnupg` folder instead.

# Exporting GPG keys
To export public keys for use with sites like GitHub, you can use the following:
`gpg --export --armor <email> --output <export_file>.gpg.pub`
Note that the `--armor` flag ensures that the output would be a readable text file as opposed to binary.

---
Related
`man gpg`
[Creating and Managing a GPG Key Pair](https://www.youtube.com/watch?v=1vVIpIvboSg)

#linux #gpg #encryption