---
layout: post
title: two different ways to enable/disable a yubikey
---

Yubikey tokens are USB devices that emit a passcode when touched.

Sometimes they accidentally generate a passcode due to accidental contact.

Here are two ways that they can be enabled/disabled so as to avoid accidental
triggering.

### Bind/unbind from USB HID driver

First, figure out the USB port for the Yubikey:

```
grep -l Yubico /sys/bus/usb/devices/*/manufacturer
```

Now, you can unbind(or bind) the various interfaces from the HID driver
(**adjust for your interfaces and choice of bind or unbind**):

```
tree /sys/bus/usb/drivers/usbhid
# Pay attention to what you're typing, dear gentle reader.
echo -n 1-2:1.0 > /sys/bus/usb/drivers/usbhid/unbind
echo -n 1-2:1.1 > /sys/bus/usb/drivers/usbhid/unbind
```

### Enable/disable as an X input device

Enable:

```
xinput set-prop "Yubico Yubikey 4 OTP+U2F" "Device Enabled" 1
```

Disable:

```
xinput set-prop "Yubico Yubikey 4 OTP+U2F" "Device Enabled" 0
```
