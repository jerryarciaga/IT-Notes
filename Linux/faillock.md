If you entered your password following a `sudo` command, it will lock you out for a set amount of time depending on how `/etc/security/faillock.conf` is configured.

To *reset* this timer, enter the following command:
`faillock --user username --reset`

---
Related:
`man 8 faillock`
[`sudo` rejects password that is correct](https://serverfault.com/questions/424775/sudo-rejects-password-that-is-correct)

#linux #bash #lockout #account 