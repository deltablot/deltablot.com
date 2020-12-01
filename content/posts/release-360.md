---
title: "What's new in eLabFTW 3.6.0"
date: 2020-12-01T02:12:55+01:00
draft: false
tags:
  - "elabftw"
  - "release"
---

I'm very pleased to announce that [eLabFTW](https://www.elabftw.net) version 3.6.0 is now available for everyone!

You can see the complete changelog on the [release page](https://github.com/elabftw/elabftw/releases/tag/3.6.0). This blog post is more about going into details for some of the changes.

# How to update

Update like usual: [see documentation](https://doc.elabftw.net/how-to-update.html).

# New features

## LDAP Authentication

It is now possible to authenticate directly using LDAP. A much awaited feature ([github issue](https://github.com/elabftw/elabftw/issues/1879)).

The documentation about this feature can be found here: https://doc.elabftw.net/ldap.html

## 2 Factor Authentication

Another great contribution by Marcel Bolten: it is now possible to require users to authenticate using 2 factors. The mechanism used is OTP and users should enable it from their profile.

![2fa](/img/2fa.png)

## Bugfixes and enhancements

The rest of the changes are mainly bugfixes and little enhancements. See [the full changelog](https://github.com/elabftw/elabftw/releases/tag/3.6.1).

## Code changes

Something that is not visible to users is how the code quality improved, as well as how tested it is. New tests have been added (both unit tests and acceptance tests simulating a user interaction through a browser). Some code have been refactored or rearranged (like all the authentication related code that is now much cleaner than before).

There is always a balance to find between adding features and working on the code itself to avoid spaghetti code and use modern coding practices (like the SOLID principles). All issues found by static analyzers are dealt with.

"Qui veut voyager loin ménage sa monture". (Slow and steady wins the race!)

# Conclusion

I would like to thank all the people that contributed to the code, opened issues and tested this new release.

Special thanks to the [sponsors](https://github.com/sponsors/NicolasCARPi)! ;)

Now go upgrade your instance and if you're not the sysadmin, ask your sysadmin to upgrade to benefit from these new features and all the bugfixes!
