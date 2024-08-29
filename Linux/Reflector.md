`reflector` is a Python script that retrieves the latest mirror list from the [Arch Linux Mirror Status](https://archlinux.org/mirrors/status/) page, sort by speed then overwrite the file `/etc/pacman.d/mirrorlist`.

Usage:
`reflector --country 'US' | sudo tee /etc/pacman.d/mirrorlist`

---

See also:
[Reflector | Arch Wiki](https://wiki.archlinux.org/title/Reflector)

Related Links:
[[Linux/pacman|pacman]]

#package-management #pacman #archlinux #linux 