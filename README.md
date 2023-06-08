Simply run make inside.

Example:
dmishura@skl:~$ git clone https://github.com/carlzhc/openbsd-netcat.git
Cloning into 'openbsd-netcat'...
remote: Enumerating objects: 78, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 78 (delta 0), reused 0 (delta 0), pack-reused 77
Unpacking objects: 100% (78/78), 61.52 KiB | 184.00 KiB/s, done.
dmishura@skl:~$
dmishura@skl:~/openbsd-netcat$ make
cc  -Iopenbsd-compat -Iopenbsd-lib -c netcat.c -o netcat.o
netcat.c: In function ‘build_ports’:
netcat.c:820:10: warning: implicit declaration of function ‘arc4random’; did you mean ‘srandom’? [-Wimplicit-function-declaration]
     y = (arc4random() & 0xFFFF) % (hi - lo);
          ^~~~~~~~~~
          srandom
cc  -Iopenbsd-compat -Iopenbsd-lib -c atomicio.c -o atomicio.o
cc  -Iopenbsd-compat -Iopenbsd-lib -c socks.c -o socks.o
cc  -Iopenbsd-compat -Iopenbsd-lib -c openbsd-lib/arc4random.c -o openbsd-lib/arc4random.o
cc  -Iopenbsd-compat -Iopenbsd-lib -c openbsd-lib/readpassphrase.c -o openbsd-lib/readpassphrase.o
cc  -Iopenbsd-compat -Iopenbsd-lib -c openbsd-compat/base64.c -o openbsd-compat/base64.o
cc  -Iopenbsd-compat -Iopenbsd-lib -c openbsd-compat/bsd-str.c -o openbsd-compat/bsd-str.o
openbsd-compat/bsd-str.c: In function ‘strtonum’:
openbsd-compat/bsd-str.c:20:21: warning: implicit declaration of function ‘strtoll’; did you mean ‘strcoll’? [-Wimplicit-function-declaration]
  long long result = strtoll (nptr, &endp, 10);
                     ^~~~~~~
                     strcoll
cc  netcat.o atomicio.o socks.o openbsd-lib/arc4random.o openbsd-lib/readpassphrase.o openbsd-compat/base64.o openbsd-compat/bsd-str.o -o nc
netcat.o: In function `main':
netcat.c:(.text+0x62c): warning: the use of `mktemp' is dangerous, better use `mkstemp' or `mkdtemp'


dmishura@ortce-skl:~/openbsd-netcat$ ls -la |grep nc
-rwxr-xr-x  1 dmishura users 48568 Jun  8 09:31 nc
-rw-r--r--  1 dmishura users 11794 Jun  8 09:31 nc.1

