## Clear NVRAM
`Command` `Option` `P` `R` keys on first boot. For more check out this article https://support.apple.com/en-us/HT204063

## Visible Names

```
$ sudo scutil --set ComputerName MacBook
$ sudo scutil --set LocalHostName MacBook
```

## Admin Account
Its basic security practice to limit the use of highly priveleged accounts for everyday use, we can solve this by creating a seperate admin account.

**If you have trouble with this follow this guide:**

Accounts can be created and managed in System Preferences. On settled systems, it is generally easier to create a second admin account and then demote the first account. This avoids data migration. Newly installed systems can also just add a standard account.

Demoting an account can be done either from the the new admin account in System Preferences – the other account must be logged out – or by executing these commands (it may not be necessary to execute both, see [issue #179](https://github.com/drduh/macOS-Security-and-Privacy-Guide/issues/179)):

```console
$ sudo dscl . -delete /Groups/admin GroupMembership <username>
$ sudo dscl . -delete /Groups/admin GroupMembers <GeneratedUID>
```

To find the “GeneratedUID” of an account:

```console
$ dscl . -read /Users/<username> GeneratedUID
```

See also [this post](https://superuser.com/a/395738) for more information about how macOS determines group membership.
