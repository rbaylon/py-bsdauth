# py-bsdauth

- Python interface to OpenBSD's BSD Auth api in libc
- Currently only implements auth_userokay(3) since this is most suitable for authenticating to OpenBSD from python

### Note
- Your application must have root privileges in order to user this application.

Usage:
```sh
>>> from bsdauth.bsdauth import UserOkay
>>> u='user1'
>>> pw='goodpassword'
>>> uo=UserOkay(u,pw)
>>> uo.login()
True
>>> pw='badpassword'
>>> uo = UserOkay(ur,pw)
>>> uo.login()
False
>>> ur='baduser'
>>> pw='goodpassword'
>>> uo = UserOkay(ur,pw)
>>> uo.login()
False
>>> exit()
```
