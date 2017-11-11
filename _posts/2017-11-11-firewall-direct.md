---
layout: post
title: Quash network traffic on Fedora
---

The default system (firewalld) is annoying--too much like windows--but you can directly add iptables rules via `firewall-cmd --direct`:

```
firewall-cmd --permanent --direct --add-rule ipv4 filter INPUT 0 -s 12.34.56.78/29 -p tcp -m tcp --dport 9000 -j ACCEPT
firewall-cmd --permanent --direct --add-rule ipv4 filter INPUT 0 -s 44.55.66.77/22 -p tcp -m tcp --dport 9000 -j ACCEPT
firewall-cmd --permanent --direct --add-rule ipv4 filter INPUT 1 -p tcp -m tcp --dport 9000 -j DROP
```

This is a very simple recipe, but should work.  Remember to test.

Reminder, permanent settings do not take affect until you restart the firewall.
