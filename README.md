ss-bash
=======

Shadowsocks traffic management script

* Only supports shadowsocks-python
* Only supports IPv4 traffic statistics

This English branch is originally translated and contributed by [@Yaoshicn](https://github.com/Yaoshicn)

[User Manual(中文)][User Manual]


[User Manual]:    https://github.com/hellofwy/ss-bash/wiki


Debug
========
ref. https://www.jianshu.com/p/8151bfd9a760 

ssserver failed to start on some distro (known Debian 9) with openssl1.1.0 which deprecated `EVP_CIPHER_CTX_cleanup`. 
(ref. https://www.openssl.org/news/cl110.txt)

Fix:
edit the file `/usr/local/lib/python2.7/dist-packages/shadowsocks/crypto/openssl.py`
replace (2 places, in line 52 and line 111) `CIPHER_CTX_cleanup` to `CIPHER_CTX_reset`

Auto Reset Usage
================
`sudo crontab -e` and add one line to reset used traffic on the first day of each month. 
`  0 0   1   *   *    /bin/sh /home/erich/ss-bash/ssadmin.sh reset_all_used`
