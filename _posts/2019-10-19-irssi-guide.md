---
layout: post
title: quick guide to setting up irssi for freenode
---

### Useful links

* https://irssi.org/documentation/startup/
* https://gist.github.com/chirag64/3c80a08a7fc1d2c52ea0
* https://wiki.archlinux.org/index.php/Irssi
* https://freenode.net/kb/answer/registration
* https://freenode.net/kb/answer/certfp
* https://www.offensive-security.com/offsec-irc-guide/
* https://minecraftonline.com/wiki/Irssi_Secure_IRC_Client

### Preface

Install `irssi` via package manager, then have a look in `/etc/irssi.conf` to
verify that they have a reasonable TLS-protected server entry for freenode.

### Client cert generation

This will allow you to bind a cert to your nick when you connect.  See the
instructions at https://freenode.net/kb/answer/certfp for more info:

```
openssl req -x509 -new -newkey rsa:4096 -sha256 -days 1000 -nodes \
  -out freenode.pem -keyout freenode.pem
openssl x509 -in freenode.pem -outform der | sha1sum -b | cut -d' ' -f1
```

Make a note of the fingerprint shown.

```
mkdir -p ~/.irssi/certs
mv freenode.pem ~/.irssi/certs
```

Also generate a random password to use for the IRC server you will connect,
and record it for safekeeping using your preferred method.

We'll refer to the following variables below:

* MyNick
* MyServerPassword
* MyJunkEmailAddress
* MyCertFile
* MyCertFingerprint
* MyRegistrationEmailToken

Each of these should be replaced with the appropriate actual string.

### Setup within irssi

```
/set real_name MyNick
/set user_name MyNick
/set nick MyNick
/set alternate_nick MyNick2
/set hilight_nick_matches_everywhere ON
/set beep_msg_level MSGS HILIGHT DCCMSGS
/server add -auto -ssl -ssl_cert MyCertFile -network freenode chat.freenode.net 6697
/connect freenode
/msg NickServ REGISTER MyServerPassword MyJunkEmailAddress
/whois MyNick
```
You should see a Z on your nick status, and the whois data should show your
client fingerprint. Go check your email, as it instructs, get the special
token, and then:
```
/msg NickServ VERIFY REGISTER MyNick MyRegistrationEmailToken
/msg NickServ cert add
/join #whatever
/ignore * joins parts quits
/save
```

### Basic commands

ctrl-n, ctrl-p to switch channel windows, page up, page down to scroll.

alt-a to go to the window with the most recent activity.

```
/join #foo  (/j for short)
/channel add -auto #foo freenode
/who  (/w for short)
/msg somebody hello  (/m for short)
/last needle
/alias abbr whatever text desired  (/al for short)
/ping
/part #foo  (/pa for short)
/win list
/win close  (/win c for short)
/win last
/win new split
/win up
/win down
```
