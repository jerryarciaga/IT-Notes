# Hardware MFA
Depending on the model, YubiKeys are hardware authentication devices created by Yubico that enhance security for accessing computers, networks, and online services. This makes it so you need more than your password to get in (something you know); you also would need a physical device (something you have).

# Features
* [FIDO](Yubikey/FIDO)
* [PIV](Yubikey/PIV)
* [OATH](Yubikey/OATH)
* [PGP](Yubikey/PGP)

# Getting Started
To use YubiKey with Linux, you need to install the the following. Package names apply for Arch Linux, so it may be named differently for other distros.
* **YubiKey Manager** `ykman` - a Python library and command-line tool for configuring and querying a YubiKey over USB.
* **YubiKey PAM-U2F** `pam-u2f` -  PAM user authentication with U2F.
* `libfido2` - Client-side U2F support. Enables web browsers to use the U2F protocol for authentication with your YubiKey.
Note that there are other optional packages you can install. These are listed in the [Arch Wiki](https://wiki.archlinux.org/title/YubiKey). 

---
Related:
`man ykman`
[YubiKey | Arch Wiki](https://wiki.archlinux.org/title/YubiKey)

#archlinux #yubikey #security