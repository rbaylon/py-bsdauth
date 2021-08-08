# py-bsdauth

- Python interface to OpenBSD's BSD Auth
- Currently only implements auth_userokay(3) since this is most suitable for authenticating to OpenBSD from python

### Note
- Your application must be in the 'auth' group to call auth_userokay(3):

```sh
usermod -G auth <yourdaemonuser>
```

For some login styles, you may also need to be in additional groups:

```sh
usermod -G _token <yourdaemonuser>  # for style in ['activ', 'crypto', 'snk', 'token']
usermod -G _radius <yourdaemonuser>  # for style == 'radius'
```
 
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
