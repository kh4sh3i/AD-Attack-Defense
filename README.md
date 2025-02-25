<h1 align="center">
  <img src="/img/logo.png" alt="" width="300px;">
  <br>
  <img src="https://img.shields.io/badge/PRs-welcome-ble">
  <img src="https://img.shields.io/github/last-commit/kh4sh3i/AD-Attack-Defense">
  <img src="https://img.shields.io/github/commit-activity/m/kh4sh3i/AD-Attack-Defense">
  <a href="https://x.com/intent/follow?screen_name=kh4sh3i_"><img src="https://img.shields.io/twitter/follow/kh4sh3i_?style=flat&logo=x"></a>
  <a href="https://github.com/kh4sh3i"><img src="https://img.shields.io/github/stars/kh4sh3i?style=flat&logo=github"></a>
</h1>


# AD-Attack-Defense
AD Attack Defense


## internal Recon

### attack
```
# check user mohsen groups
net user mohsen /domain

# check with user is in DA:
net group "domain admins" /domain
```

### defence 
```
we can disable SAM protocol for prevent call net user function for local user
we make GPO with name sam_disable and assign to domain admin
we sent below policie and only admin can call this function

gpupdate /force
```
<img src="/img/1.png" alt="" width="100%;">
<img src="/img/2.png" alt="" width="100%;">



### bypass 
```
attacker use ADSI query !

([adsisearcher]"(&(objectCategory=group)(cn=Domain Admins))").FindAll() | ForEach-Object {$_.Properties.member}
```


