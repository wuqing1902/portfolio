# Krypton - cryptography

## Krypton 0
### Level Info
Welcome to Krypton! The first level is easy. The following string encodes the password using Base64:

S1JZUFRPTklTR1JFQVQ=
Use this password to log in to krypton.labs.overthewire.org with username krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ echo 'S1JZUFRPTklTR1JFQVQ=' | base64 -d
KRYPTONISGREAT 
```


<br><br><br><br><br>





## Krypton 1
### Level Info
The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation. It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton1@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
krypton1@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton1@krypton:~$ cd /krypton
krypton1@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton1@krypton:/krypton$ cd krypton1
krypton1@krypton:/krypton/krypton1$ ls
krypton2  README
krypton1@krypton:/krypton/krypton1$ cat README 
Welcome to Krypton!

This game is intended to give hands on experience with cryptography
and cryptanalysis.  The levels progress from classic ciphers, to modern,
easy to harder.

Although there are excellent public tools, like cryptool,to perform
the simple analysis, we strongly encourage you to try and do these
without them for now.  We will use them in later excercises.

** Please try these levels without cryptool first **


The first level is easy.  The password for level 2 is in the file 
'krypton2'.  It is 'encrypted' using a simple rotation called ROT13.  
It is also in non-standard ciphertext format.  When using alpha characters for
cipher text it is normal to group the letters into 5 letter clusters, 
regardless of word boundaries.  This helps obfuscate any patterns.

This file has kept the plain text word boundaries and carried them to
the cipher text.

Enjoy!
krypton1@krypton:/krypton/krypton1$ cat krypton2 
YRIRY GJB CNFFJBEQ EBGGRA
krypton1@krypton:/krypton/krypton1$ cat krypton2 | tr 'A-Z' 'N-ZA-O'
LEVEL TWO PASSWORD ROTTEN
krypton1@krypton:/krypton/krypton1$ exit
logout
Connection to krypton.labs.overthewire.org closed.
```



<br><br><br><br><br>






## Krypton 2
### Level Info
ROT13 is a simple substitution cipher.

Substitution ciphers are a simple replacement algorithm. In this example of a substitution cipher, we will explore a ‘monoalphebetic’ cipher. Monoalphebetic means, literally, “one alphabet” and you will see why.

This level contains an old form of cipher called a ‘Caesar Cipher’. A Caesar cipher shifts the alphabet by a set number. For example:

plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...
In this example, the letter ‘a’ in plaintext is replaced by a ‘G’ in the ciphertext so, for example, the plaintext ‘bad’ becomes ‘HGJ’ in ciphertext.

The password for level 3 is in the file krypton3. It is in 5 letter group ciphertext. It is encrypted with a Caesar Cipher. Without any further information, this cipher text may be difficult to break. You do not have direct access to the key, however you do have access to a program that will encrypt anything you wish to give it using the key. If you think logically, this is completely easy.

One shot can solve it!

Have fun.

Additional Information:

The encrypt binary will look for the keyfile in your current working directory. Therefore, it might be best to create a working direcory in /tmp and in there a link to the keyfile. As the encrypt binary runs setuid krypton3, you also need to give krypton3 access to your working directory.

Here is an example:

krypton2@melinda:~$ mktemp -d
/tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
ciphertext  keyfile.dat

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton2@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
krypton2@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton2@krypton:~$ krypton2@krypton:~$ cd /krypton
krypton2@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton2@krypton:/krypton$ cd krypton2
krypton2@krypton:/krypton/krypton2$ ls 
encrypt  keyfile.dat  krypton3  README
krypton2@krypton:/krypton/krypton2$ cat README 
Krypton 2

ROT13 is a simple substitution cipher.

Substitution ciphers are a simple replacement algorithm.  In this example
of a substitution cipher, we will explore a 'monoalphebetic' cipher.
Monoalphebetic means, literally, "one alphabet" and you will see why.

This level contains an old form of cipher called a 'Caesar Cipher'.
A Caesar cipher shifts the alphabet by a set number.  For example:

plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...

In this example, the letter 'a' in plaintext is replaced by a 'G' in the
ciphertext so, for example, the plaintext 'bad' becomes 'HGJ' in ciphertext.

The password for level 3 is in the file krypton3.  It is in 5 letter
group ciphertext.  It is encrypted with a Caesar Cipher.  Without any 
further information, this cipher text may be difficult to break.  You do 
not have direct access to the key, however you do have access to a program 
that will encrypt anything you wish to give it using the key.  
If you think logically, this is completely easy.

One shot can solve it!

Have fun.

Additional Information:

The `encrypt` binary will look for the keyfile in your current working
directory. Therefore, it might be best to create a working direcory in /tmp
and in there a link to the keyfile. As the `encrypt` binary runs setuid
`krypton3`, you also need to give `krypton3` access to your working directory.

Here is an example:

krypton2@melinda:~$ mktemp -d
/tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
ciphertext  keyfile.dat

krypton2@krypton:/krypton/krypton2$ mktemp -d
/tmp/tmp.2nlpntMLhA
krypton2@krypton:/krypton/krypton2$ cd /tmp/tmp.2nlpntMLhA
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ ln -s /krypton/krypton2/keyfile.dat
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ ls
keyfile.dat
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ chmod 777 .
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ /krypton/krypton2/encrypt /etc/issue
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ ls
ciphertext  keyfile.dat
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ cat ciphertext
GNGZFGXFEZXNMOWQZPUZGEQSUNEAZ
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ /krypton/krypton2/encrypt

 usage: encrypt foo  - where foo is the file containing the plaintext
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ vi plaintext
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ cat plaintext 
ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ /krypton/krypton2/encrypt plaintext 
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ ls
ciphertext  keyfile.dat  plaintext
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ cat ciphertext 
MNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKL
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ cat /krypton/krypton2/krypton3
OMQEMDUEQMEK
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ cat /krypton/krypton2/krypton3 | tr 'M-ZA-L' 'A-Z'
CAESARISEASY
krypton2@krypton:/tmp/tmp.2nlpntMLhA$ exit
logout
Connection to krypton.labs.overthewire.org closed.
```



<br><br><br><br><br>






## Krypton 3
### Level Info
Well done. You’ve moved past an easy substitution cipher.

The main weakness of a simple substitution cipher is repeated use of a simple key. In the previous exercise you were able to introduce arbitrary plaintext to expose the key. In this example, the cipher mechanism is not available to you, the attacker.

However, you have been lucky. You have intercepted more than one message. The password to the next level is found in the file ‘krypton4’. You have also found 3 other files. (found1, found2, found3)

You know the following important details:

The message plaintexts are in American English (*** very important) - They were produced from the same key (*** even better!)
Enjoy.

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton3@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
krypton3@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton3@krypton:~$ cd /krypton/
krypton3@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton3@krypton:/krypton$ cd krypton3
krypton3@krypton:/krypton/krypton3$ ls
found1  found2  found3  HINT1  HINT2  krypton4  README
krypton3@krypton:/krypton/krypton3$ cat README 
Well done.  You've moved past an easy substitution cipher.

Hopefully you just encrypted the alphabet a plaintext 
to fully expose the key in one swoop.

The main weakness of a simple substitution cipher is 
repeated use of a simple key.  In the previous exercise
you were able to introduce arbitrary plaintext to expose
the key.  In this example, the cipher mechanism is not 
available to you, the attacker.

However, you have been lucky.  You have intercepted more
than one message.  The password to the next level is found
in the file 'krypton4'.  You have also found 3 other files.
(found1, found2, found3)

You know the following important details:

- The message plaintexts are in English (*** very important)
- They were produced from the same key (*** even better!)


Enjoy.


krypton3@krypton:/krypton/krypton3$ cat HINT1
Some letters are more prevalent in English than others.
krypton3@krypton:/krypton/krypton3$ cat HINT2
"Frequency Analysis" is your friend.
krypton3@krypton:/krypton/krypton3$ cat found1
CGZNL YJBEN QYDLQ ZQSUQ NZCYD SNQVU BFGBK GQUQZ QSUQN UZCYD SNJDS UDCXJ ZCYDS NZQSU QNUZB WSBNZ QSUQN UDCXJ CUBGS BXJDS UCTYV SUJQG WTBUJ KCWSV LFGBK GSGZN LYJCB GJSZD GCHMS UCJCU QJLYS BXUMA UJCJM JCBGZ CYDSN CGKDC ZDSQZ DVSJJ SNCGJ DSYVQ CGJSO JCUNS YVQZS WALQV SJJSN UBTSX COSWG MTASN BXYBU CJCBG UWBKG JDSQV YDQAS JXBNS OQTYV SKCJD QUDCX JBXQK BMVWA SNSYV QZSWA LWAKB MVWAS ZBTSS QGWUB BGJDS TSJDB WCUGQ TSWQX JSNRM VCMUZ QSUQN KDBMU SWCJJ BZBTT MGCZQ JSKCJ DDCUE SGSNQ VUJDS SGZNL YJCBG UJSYY SNXBN TSWAL QZQSU QNZCY DSNCU BXJSG CGZBN YBNQJ SWQUY QNJBX TBNSZ BTYVS OUZDS TSUUM ZDQUJ DSICE SGNSZ CYDSN QGWUJ CVVDQ UTBWS NGQYY VCZQJ CBGCG JDSNB JULUJ STQUK CJDQV VUCGE VSQVY DQASJ UMAUJ CJMJC BGZCY DSNUJ DSZQS UQNZC YDSNC USQUC VLANB FSGQG WCGYN QZJCZ SBXXS NUSUU SGJCQ VVLGB ZBTTM GCZQJ CBGUS ZMNCJ LUDQF SUYSQ NSYNB WMZSW TBUJB XDCUF GBKGK BNFAS JKSSG QGWDC USQNV LYVQL UKSNS TQCGV LZBTS WCSUQ GWDCU JBNCS UESGN SUDSN QCUSW JBJDS YSQFB XUBYD CUJCZ QJCBG QGWQN JCUJN LALJD SSGWB XJDSU COJSS GJDZS GJMNL GSOJD SKNBJ STQCG VLJNQ ESWCS UMGJC VQABM JCGZV MWCGE DQTVS JFCGE VSQNQ GWTQZ ASJDZ BGUCW SNSWU BTSBX JDSXC GSUJS OQTYV SUCGJ DSSGE VCUDV QGEMQ ESCGD CUVQU JYDQU SDSKN BJSJN QECZB TSWCS UQVUB FGBKG QUNBT QGZSU QGWZB VVQAB NQJSW KCJDB JDSNY VQLKN CEDJU TQGLB XDCUY VQLUK SNSYM AVCUD SWCGS WCJCB GUBXI QNLCG EHMQV CJLQG WQZZM NQZLW MNCGE DCUVC XSJCT SQGWC GJKBB XDCUX BNTSN JDSQJ NCZQV ZBVVS QEMSU YMAVC UDSWJ DSXCN UJXBV CBQZB VVSZJ SWSWC JCBGB XDCUW NQTQJ CZKBN FUJDQ JCGZV MWSWQ VVAMJ JKBBX JDSYV QLUGB KNSZB EGCUS WQUUD QFSUY SQNSU
krypton3@krypton:/krypton/krypton3$ cat found2
QVJDB MEDGB QJJSG WQGZS NSZBN WUXBN JDSYS NCBWU MNICI STBUJ ACBEN QYDSN UQENS SJDQJ UDQFS UYSQN SKQUS WMZQJ SWQJJ DSFCG EUGSK UZDBB VCGUJ NQJXB NWQXN SSUZD BBVZD QNJSN SWCGQ ABMJQ HMQNJ SNBXQ TCVSX NBTDC UDBTS ENQTT QNUZD BBVUI QNCSW CGHMQ VCJLW MNCGE JDSSV CPQAS JDQGS NQAMJ JDSZM NNCZM VMTKQ UWCZJ QJSWA LVQKJ DNBME DBMJS GEVQG WQGWJ DSUZD BBVKB MVWDQ ISYNB ICWSW QGCGJ SGUCI SSWMZ QJCBG CGVQJ CGENQ TTQNQ GWJDS ZVQUU CZUQJ JDSQE SBXUD QFSUY SQNST QNNCS WJDSL SQNBV WQGGS DQJDQ KQLJD SZBGU CUJBN LZBMN JBXJD SWCBZ SUSBX KBNZS UJSNC UUMSW QTQNN CQESV CZSGZ SBGGB ISTAS NJKBB XDQJD QKQLU GSCED ABMNU YBUJS WABGW UJDSG SOJWQ LQUUM NSJLJ DQJJD SNSKS NSGBC TYSWC TSGJU JBJDS TQNNC QESJD SZBMY VSTQL DQISQ NNQGE SWJDS ZSNST BGLCG UBTSD QUJSU CGZSJ DSKBN ZSUJS NZDQG ZSVVB NQVVB KSWJD STQNN CQESA QGGUJ BASNS QWBGZ SCGUJ SQWBX JDSMU MQVJD NSSJC TSUQG GSUYN SEGQG ZLZBM VWDQI SASSG JDSNS QUBGX BNJDC UUCOT BGJDU QXJSN JDSTQ NNCQE SUDSE QISAC NJDJB QWQME DJSNU MUQGG QKDBK QUAQY JCUSW BGTQL JKCGU UBGDQ TGSJQ GWWQM EDJSN RMWCJ DXBVV BKSWQ VTBUJ JKBLS QNUVQ JSNQG WKSNS AQYJC USWBG XSANM QNLDQ TGSJW CSWBX MGFGB KGZQM USUQJ JDSQE SBXQG WKQUA MNCSW BGQME MUJQX JSNJD SACNJ DBXJD SJKCG UJDSN SQNSX SKDCU JBNCZ QVJNQ ZSUBX UDQFS UYSQN SMGJC VDSCU TSGJC BGSWQ UYQNJ BXJDS VBGWB GJDSQ JNSUZ SGSCG ASZQM USBXJ DCUEQ YUZDB VQNUN SXSNJ BJDSL SQNUA SJKSS GQGWQ UUDQF SUYSQ NSUVB UJLSQ NUACB ENQYD SNUQJ JSTYJ CGEJB QZZBM GJXBN JDCUY SNCBW DQISN SYBNJ SWTQG LQYBZ NLYDQ VUJBN CSUGC ZDBVQ UNBKS UDQFS UYSQN SUXCN UJACB ENQYD SNNSZ BMGJS WQUJN QJXBN WVSES GWJDQ JUDQF SUYSQ NSXVS WJDSJ BKGXB NVBGW BGJBS UZQYS YNBUS ZMJCB GXBNW SSNYB QZDCG EQGBJ DSNSC EDJSS GJDZS GJMNL UJBNL DQUUD QFSUY SQNSU JQNJC GEDCU JDSQJ NCZQV ZQNSS NTCGW CGEJD SDBNU SUBXJ DSQJN SYQJN BGUCG VBGWB GRBDG QMANS LNSYB NJSWJ DQJUD QFSUY SQNSD QWASS GQZBM GJNLU ZDBBV TQUJS NUBTS JKSGJ CSJDZ SGJMN LUZDB VQNUD QISUM EESUJ SWJDQ JUDQF SUYSQ NSTQL DQISA SSGST YVBLS WQUQU ZDBBV TQUJS NALQV SOQGW SNDBE DJBGB XVQGZ QUDCN SQZQJ DBVCZ VQGWB KGSNK DBGQT SWQZS NJQCG KCVVC QTUDQ FSUDQ XJSCG DCUKC VVGBS ICWSG ZSUMA UJQGJ CQJSU UMZDU JBNCS UBJDS NJDQG DSQNU QLZBV VSZJS WQXJS NDCUW SQJD
krypton3@krypton:/krypton/krypton3$ cat found3
DSNSM YBGVS ENQGW QNBUS KCJDQ ENQIS QGWUJ QJSVL QCNQG WANBM EDJTS JDSAS SJVSX NBTQE VQUUZ QUSCG KDCZD CJKQU SGZVB USWCJ KQUQA SQMJC XMVUZ QNQAQ SMUQG WQJJD QJJCT SMGFG BKGJB GQJMN QVCUJ UBXZB MNUSQ ENSQJ YNCPS CGQUZ CSGJC XCZYB CGJBX ICSKJ DSNSK SNSJK BNBMG WAVQZ FUYBJ UGSQN BGSSO JNSTC JLBXJ DSAQZ FQGWQ VBGEB GSGSQ NJDSB JDSNJ DSUZQ VSUKS NSSOZ SSWCG EVLDQ NWQGW EVBUU LKCJD QVVJD SQYYS QNQGZ SBXAM NGCUD SWEBV WJDSK SCEDJ BXJDS CGUSZ JKQUI SNLNS TQNFQ AVSQG WJQFC GEQVV JDCGE UCGJB ZBGUC WSNQJ CBGCZ BMVWD QNWVL AVQTS RMYCJ SNXBN DCUBY CGCBG NSUYS ZJCGE CJ
krypton3@krypton:/krypton/krypton3$ cat krypton4
KSVVW BGSJD SVSIS VXBMN YQUUK BNWCU ANMJS
krypton3@krypton:/krypton/krypton3$ exit
logout
Connection to krypton.labs.overthewire.org closed.
```

go to the website `https://quipqiup.com/` to decrypt the ciphertext. 
ciphertext found1:
```
CGZNL YJBEN QYDLQ ZQSUQ NZCYD SNQVU BFGBK GQUQZ QSUQN UZCYD SNJDS UDCXJ ZCYDS NZQSU QNUZB WSBNZ QSUQN UDCXJ CUBGS BXJDS UCTYV SUJQG WTBUJ KCWSV LFGBK GSGZN LYJCB GJSZD GCHMS UCJCU QJLYS BXUMA UJCJM JCBGZ CYDSN CGKDC ZDSQZ DVSJJ SNCGJ DSYVQ CGJSO JCUNS YVQZS WALQV SJJSN UBTSX COSWG MTASN BXYBU CJCBG UWBKG JDSQV YDQAS JXBNS OQTYV SKCJD QUDCX JBXQK BMVWA SNSYV QZSWA LWAKB MVWAS ZBTSS QGWUB BGJDS TSJDB WCUGQ TSWQX JSNRM VCMUZ QSUQN KDBMU SWCJJ BZBTT MGCZQ JSKCJ DDCUE SGSNQ VUJDS SGZNL YJCBG UJSYY SNXBN TSWAL QZQSU QNZCY DSNCU BXJSG CGZBN YBNQJ SWQUY QNJBX TBNSZ BTYVS OUZDS TSUUM ZDQUJ DSICE SGNSZ CYDSN QGWUJ CVVDQ UTBWS NGQYY VCZQJ CBGCG JDSNB JULUJ STQUK CJDQV VUCGE VSQVY DQASJ UMAUJ CJMJC BGZCY DSNUJ DSZQS UQNZC YDSNC USQUC VLANB FSGQG WCGYN QZJCZ SBXXS NUSUU SGJCQ VVLGB ZBTTM GCZQJ CBGUS ZMNCJ LUDQF SUYSQ NSYNB WMZSW TBUJB XDCUF GBKGK BNFAS JKSSG QGWDC USQNV LYVQL UKSNS TQCGV LZBTS WCSUQ GWDCU JBNCS UESGN SUDSN QCUSW JBJDS YSQFB XUBYD CUJCZ QJCBG QGWQN JCUJN LALJD SSGWB XJDSU COJSS GJDZS GJMNL GSOJD SKNBJ STQCG VLJNQ ESWCS UMGJC VQABM JCGZV MWCGE DQTVS JFCGE VSQNQ GWTQZ ASJDZ BGUCW SNSWU BTSBX JDSXC GSUJS OQTYV SUCGJ DSSGE VCUDV QGEMQ ESCGD CUVQU JYDQU SDSKN BJSJN QECZB TSWCS UQVUB FGBKG QUNBT QGZSU QGWZB VVQAB NQJSW KCJDB JDSNY VQLKN CEDJU TQGLB XDCUY VQLUK SNSYM AVCUD SWCGS WCJCB GUBXI QNLCG EHMQV CJLQG WQZZM NQZLW MNCGE DCUVC XSJCT SQGWC GJKBB XDCUX BNTSN JDSQJ NCZQV ZBVVS QEMSU YMAVC UDSWJ DSXCN UJXBV CBQZB VVSZJ SWSWC JCBGB XDCUW NQTQJ CZKBN FUJDQ JCGZV MWSWQ VVAMJ JKBBX JDSYV QLUGB KNSZB EGCUS WQUUD QFSUY SQNSU
```
plaintext found1:
```
in cryptography a caesar cipher also known as a caesars cipher the shift cipher caesars code or caesar shift is one of the simplest and most widely known encryption techniques it is a type of substitution cipher in which each letter in the plain text is replaced by a letter some fixed number of positions down the alphabet for example with a shift of a would be replaced by db would become e and soon the method is named after julius caesar who used it to communicate with his generals the encryption step performed by a caesar cipher is often incorporated as part of more complex schemes such as the vigenre cipher and still has modern application in the rot system as with all single alphabet substitution ciphers the caesar cipher is easily broken and in practice offers essentially no communication security shakespeare produced most of his known work between and his early plays were mainly comedies and histories genre she raised to the peak of sophistication and artistry by the end of the sixteenth century next he wrote mainly tragedies until about including hamlet king lear and macbeth considered some of the finest examples in the english language in his last phase he wrote tragicomedies also known as romances and collaborated with other playwrights many of his plays were published in editions of varying quality and accuracy during his lifetime and in two of his former theatrical colleagues published the first folio a collected edition of his dramatic works that included all but two of the plays now recognised as shakespeares
```

ciphertext found2:
```
QVJDB MEDGB QJJSG WQGZS NSZBN WUXBN JDSYS NCBWU MNICI STBUJ ACBEN QYDSN UQENS SJDQJ UDQFS UYSQN SKQUS WMZQJ SWQJJ DSFCG EUGSK UZDBB VCGUJ NQJXB NWQXN SSUZD BBVZD QNJSN SWCGQ ABMJQ HMQNJ SNBXQ TCVSX NBTDC UDBTS ENQTT QNUZD BBVUI QNCSW CGHMQ VCJLW MNCGE JDSSV CPQAS JDQGS NQAMJ JDSZM NNCZM VMTKQ UWCZJ QJSWA LVQKJ DNBME DBMJS GEVQG WQGWJ DSUZD BBVKB MVWDQ ISYNB ICWSW QGCGJ SGUCI SSWMZ QJCBG CGVQJ CGENQ TTQNQ GWJDS ZVQUU CZUQJ JDSQE SBXUD QFSUY SQNST QNNCS WJDSL SQNBV WQGGS DQJDQ KQLJD SZBGU CUJBN LZBMN JBXJD SWCBZ SUSBX KBNZS UJSNC UUMSW QTQNN CQESV CZSGZ SBGGB ISTAS NJKBB XDQJD QKQLU GSCED ABMNU YBUJS WABGW UJDSG SOJWQ LQUUM NSJLJ DQJJD SNSKS NSGBC TYSWC TSGJU JBJDS TQNNC QESJD SZBMY VSTQL DQISQ NNQGE SWJDS ZSNST BGLCG UBTSD QUJSU CGZSJ DSKBN ZSUJS NZDQG ZSVVB NQVVB KSWJD STQNN CQESA QGGUJ BASNS QWBGZ SCGUJ SQWBX JDSMU MQVJD NSSJC TSUQG GSUYN SEGQG ZLZBM VWDQI SASSG JDSNS QUBGX BNJDC UUCOT BGJDU QXJSN JDSTQ NNCQE SUDSE QISAC NJDJB QWQME DJSNU MUQGG QKDBK QUAQY JCUSW BGTQL JKCGU UBGDQ TGSJQ GWWQM EDJSN RMWCJ DXBVV BKSWQ VTBUJ JKBLS QNUVQ JSNQG WKSNS AQYJC USWBG XSANM QNLDQ TGSJW CSWBX MGFGB KGZQM USUQJ JDSQE SBXQG WKQUA MNCSW BGQME MUJQX JSNJD SACNJ DBXJD SJKCG UJDSN SQNSX SKDCU JBNCZ QVJNQ ZSUBX UDQFS UYSQN SMGJC VDSCU TSGJC BGSWQ UYQNJ BXJDS VBGWB GJDSQ JNSUZ SGSCG ASZQM USBXJ DCUEQ YUZDB VQNUN SXSNJ BJDSL SQNUA SJKSS GQGWQ UUDQF SUYSQ NSUVB UJLSQ NUACB ENQYD SNUQJ JSTYJ CGEJB QZZBM GJXBN JDCUY SNCBW DQISN SYBNJ SWTQG LQYBZ NLYDQ VUJBN CSUGC ZDBVQ UNBKS UDQFS UYSQN SUXCN UJACB ENQYD SNNSZ BMGJS WQUJN QJXBN WVSES GWJDQ JUDQF SUYSQ NSXVS WJDSJ BKGXB NVBGW BGJBS UZQYS YNBUS ZMJCB GXBNW SSNYB QZDCG EQGBJ DSNSC EDJSS GJDZS GJMNL UJBNL DQUUD QFSUY SQNSU JQNJC GEDCU JDSQJ NCZQV ZQNSS NTCGW CGEJD SDBNU SUBXJ DSQJN SYQJN BGUCG VBGWB GRBDG QMANS LNSYB NJSWJ DQJUD QFSUY SQNSD QWASS GQZBM GJNLU ZDBBV TQUJS NUBTS JKSGJ CSJDZ SGJMN LUZDB VQNUD QISUM EESUJ SWJDQ JUDQF SUYSQ NSTQL DQISA SSGST YVBLS WQUQU ZDBBV TQUJS NALQV SOQGW SNDBE DJBGB XVQGZ QUDCN SQZQJ DBVCZ VQGWB KGSNK DBGQT SWQZS NJQCG KCVVC QTUDQ FSUDQ XJSCG DCUKC VVGBS ICWSG ZSUMA UJQGJ CQJSU UMZDU JBNCS UBJDS NJDQG DSQNU QLZBV VSZJS WQXJS NDCUW SQJD
```

plaintext found2:
```
although no attendance records for the period survive most biographers agree that shakespeare was educated at the kings new school in stratford a free school chartered in about a quarter of a mile from his home grammar schools varied in quality during the elizabethan era but the curriculum was dictated by law throughout england and the school would have provided an intensive education in latin grammar and the classics at the age of shakespeare married the year old anne hathaway the consistory court of the diocese of worcester issued a marriage licence on november two of hathaways neighbours posted bonds the next day as surety that there were no impediments to the marriage the couple may have arranged the ceremony in some haste since the worcester chancellor allowed the marriage banns to be read once instead of the usual three times annes pregnancy could have been the reason for this six months after the marriage she gave birth to a daughter susanna who was baptised on may twins son hamnet and daughter judith followed almost two years later and were baptised on february ham net died of unknown causes at the age of and was buried on august after the birth of the twins there are few historical traces of shakespeare until he is mentioned as part of the london theatre scene in because of this gap scholars refer to the years between and as shakespeares lost years biographers attempting to account for this period have reported many apocryphal stories nicholas rowe shakespeares first biographer recounted a stratford legend that shakespeare fled the town for london to escape prosecution for deer poaching another eighteenth century story has shakespeare starting his theatrical career minding the horses of theatre patrons in london john aubrey reported that shakespeare had been a country school master some twentieth century scholars have suggested that shakespeare may have been employed as a schoolmaster by alexander hoghton of lancashire a catholic landowner who named a certain william shakesh aftein his will no evidence substantiates such stories other than hearsay collected after his death
```

ciphertext found3:
```
DSNSM YBGVS ENQGW QNBUS KCJDQ ENQIS QGWUJ QJSVL QCNQG WANBM EDJTS JDSAS SJVSX NBTQE VQUUZ QUSCG KDCZD CJKQU SGZVB USWCJ KQUQA SQMJC XMVUZ QNQAQ SMUQG WQJJD QJJCT SMGFG BKGJB GQJMN QVCUJ UBXZB MNUSQ ENSQJ YNCPS CGQUZ CSGJC XCZYB CGJBX ICSKJ DSNSK SNSJK BNBMG WAVQZ FUYBJ UGSQN BGSSO JNSTC JLBXJ DSAQZ FQGWQ VBGEB GSGSQ NJDSB JDSNJ DSUZQ VSUKS NSSOZ SSWCG EVLDQ NWQGW EVBUU LKCJD QVVJD SQYYS QNQGZ SBXAM NGCUD SWEBV WJDSK SCEDJ BXJDS CGUSZ JKQUI SNLNS TQNFQ AVSQG WJQFC GEQVV JDCGE UCGJB ZBGUC WSNQJ CBGCZ BMVWD QNWVL AVQTS RMYCJ SNXBN DCUBY CGCBG NSUYS ZJCGE CJ
```

plaintext found3:
```
hereupon le grand arose with a grave and stately air and brought me the beetle from a glass case in which it was enclosed it was a beautiful scarabaeus and at that time unknown to naturalists of course a great prize in a scientific point of view there were two round black spots near one extremity of the back and a long one near the other the scales were exceedingly hard and glossy with all the appearance of burnished gold the weight of the insect was very remarkable and taking all things into consideration i could hardly blame jupiter for his opinion respecting it
```

ciphertext krypton4:
```
KSVVW BGSJD SVSIS VXBMN YQUUK BNWCU ANMJS
```

plaintext krypton4:
```
well done the level four password is brute
```

password is `BRUTE` for next level

<br><br><br><br><br>






## Krypton 4
### Level Info
Good job!

You more than likely used some form of FA and some common sense to solve that one.

So far we have worked with simple substitution ciphers. They have also been ‘monoalphabetic’, meaning using a fixed key, and giving a one to one mapping of plaintext (P) to ciphertext (C). Another type of substitution cipher is referred to as ‘polyalphabetic’, where one character of P may map to many, or all, possible ciphertext characters.

An example of a polyalphabetic cipher is called a Vigenère Cipher. It works like this:

If we use the key(K) ‘GOLD’, and P = PROCEED MEETING AS AGREED, then “add” P to K, we get C. When adding, if we exceed 25, then we roll to 0 (modulo 26).

P P R O C E E D M E E T I N G A S A G R E E D\
K G O L D G O L D G O L D G O L D G O L D G O\
becomes:

P 15 17 14 2 4 4 3 12 4 4 19 8 13 6 0 18 0 6 17 4 4 3\
K 6 14 11 3 6 14 11 3 6 14 11 3 6 14 11 3 6 14 11 3 6 14\
C 21 5 25 5 10 18 14 15 10 18 4 11 19 20 11 21 6 20 2 8 10 17\
So, we get a ciphertext of:

VFZFK SOPKS ELTUL VGUCH KR
This level is a Vigenère Cipher. You have intercepted two longer, english language messages (American English). You also have a key piece of information. You know the key length!

For this exercise, the key length is 6. The password to level five is in the usual place, encrypted with the 6 letter key.

Have fun!

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton4@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
krypton4@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton4@krypton:~$ cd /krypton/
krypton4@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton4@krypton:/krypton$ cd krypton4
krypton4@krypton:/krypton/krypton4$ ls
found1  found2  HINT  krypton5  README
krypton4@krypton:/krypton/krypton4$ cat README 
Good job!

You more than likely used frequency analysis and some common sense
to solve that one.

So far we have worked with simple substitution ciphers.  They have
also been 'monoalphabetic', meaning using a fixed key, and 
giving a one to one mapping of plaintext (P) to ciphertext (C).
Another type of substitution cipher is referred to as 'polyalphabetic',
where one character of P may map to many, or all, possible ciphertext 
characters.

An example of a polyalphabetic cipher is called a Vigen�re Cipher.  It works
like this:

If we use the key(K)  'GOLD', and P = PROCEED MEETING AS AGREED, then "add"
P to K, we get C.  When adding, if we exceed 25, then we roll to 0 (modulo 26).


P     P R O C E   E D M E E   T I N G A   S A G R E   E D
K     G O L D G   O L D G O   L D G O L   D G O L D   G O

becomes:

P     15 17 14 2  4  4  3 12  4 4  19  8 13 6  0  18 0  6 17 4 4   3
K     6  14 11 3  6 14 11  3  6 14 11  3  6 14 11  3 6 14 11 3 6  14
C     21 5  25 5 10 18 14 15 10 18  4 11 19 20 11 21 6 20  2 8 10 17

So, we get a ciphertext of:

VFZFK SOPKS ELTUL VGUCH KR

This level is a Vigen�re Cipher.  You have intercepted two longer, english 
language messages.  You also have a key piece of information.  You know the 
key length!

For this exercise, the key length is 6.  The password to level five is in the usual
place, encrypted with the 6 letter key.

Have fun!
krypton4@krypton:/krypton/krypton4$ cat HINT 
Frequency analysis will still work, but you need to analyse it
by "keylength".  Analysis of cipher text at position 1, 7, 13, etc
should reveal the 1st letter of the key, in this case.  Treat this as
6 different mono-alphabetic ciphers...

Persistence and some good guesses are the key!
krypton4@krypton:/krypton/krypton4$ cat found1
YYICS JIZIB AGYYX RIEWV IXAFN JOOVQ QVHDL CRKLB SSLYX RIQYI IOXQT WXRIC RVVKP BHZXI YLYZP DLCDI IKGFJ UXRIP TFQGL CWVXR IEZRV NMYSF JDLCL RXOWJ NMINX FNJSP JGHVV ERJTT OOHRM VMBWN JTXKG JJJXY TSYKL OQZFT OSRFN JKBIY YSSHE LIKLO RFJGS VMRJC CYTCS VHDLC LRXOJ MWFYB JPNVR NWUMZ GRVMF UPOEB XKSDL CBZGU IBBZX MLMKK LOACX KECOC IUSBS RMPXR IPJZW XSPTR HKRQB VVOHR MVKEE PIZEX SDYYI QERJJ RYSLJ VZOVU NJLOW RTXSD LYYNE ILMBK LORYW VAOXM KZRNL CWZRA YGWVH DLCLZ VVXFF KASPJ GVIKW WWVTV MCIKL OQYSW SBAFJ EWRII SFACC MZRVO MLYYI MSSSK VISDY YIGML PZICW FJNMV PDNEH ISSFE HWEIJ PSEEJ QYIBW JFMIC TCWYE ZWLTK WKMBY YICGY WVGBS UKFVG IKJRR DSBJJ XBSWM VVYLR MRXSW BNWJO VCSKW KMBYY IQYYW UMKRM KKLOK YYVWX SMSVL KWCAV VNIQY ISIIB MVVLI DTIIC SGSRX EVYQC CDLMZ XLDWF JNSEP BRROO WJFMI CSDDF YKWQM VLKWM KKLOV CXKFE XRFBI MEPJW SBWFJ ZWGMA PVHKR BKZIB GCFEH WEWSF XKPJT NCYYR TUICX PTPLO VIJVT DSRMV AOWRB YIBIR MVWER QJKWK RBDFY MELSF XPEGQ KSPML IYIBX FJPXR ELPVH RMKFE HLEBJ YMWKM TUFII YSUXE VLJUX YAYWU XRIUJ JXGEJ PZRQS TJIJS IJIJS PWMKK KBEQX USDXC IYIBI YSUXR IPJNM DLBFZ WSIQF EHLYR YVVMY NXUSB SRMPW DMJQN SBIRM VTBIR YPWSP IIIIC WQMVL KHNZK SXMLY YIZEJ FTILY RSFAD SFJIW EVNWZ WOWFJ WSERB NKAKW LTCSX KCWXV OILGL XZYPJ NLSXC YYIBM ZGFRK VMZEH DSRTJ ROGIM RHKPQ TCSCX GYJKB ICSTS VSPFE HGEQF JARMR JRWNS PTKLI WBWVW CXFJV QOVYQ UGSXW BRWCS MSCIP XDFIF OLGSU ECXFJ PENZY STINX FJXVY YLISI MEKJI SEKFJ IEXHF NCPSI PKFVD LCWVA OVCSF JKVKX ESBLM ZJICM LYYMC GMZEX BCMKK LOACX KEXHR MVKBS SSUAK WSSKM VPCIZ RDLCF WXOVL TFRDL CXLRC LMSVL YXGSK LOMPK RGOWD TIXRI PJNIB ILTKV OIQYF SPJCW KLOQQ MRHOW MYYED FCKFV ORGLY XNSPT KLIEL IKSDS YSUXR IJNFR GIPJK MBIBF EHVEW IFAXY NTEXR IEWRW CELIW IVPYX CIOTU NKLDL CBFSN QYSRR NXFJJ GKVCH ISGOC JGMXK UFKGR
krypton4@krypton:/krypton/krypton4$ cat found2
YYIIA CWVSL PGLVH DSAFD TYYRY YEDRG LYXER BJIEV EPLVX BICNE XRIDT IICXD TIXRI PJNIB ILTYS EWCXE IKVRM VXBIC RRHOE ETFHD LGHBG YZCWZ RQXMU ISDIA YKLOQ DWFQD LCIVA KRBYY IDMLB FSNQY STLYT NJUEQ VCFKT SPCTW AYSBB ZXRLG XRBOE LIUSB SRMPF EMJYR WZPCS UMNJG WVXRE RBRVW IBMVV KRBRR HOLCW WIOPJ JJWVS LJCCC LCFEH DSRTR XOXFJ CECXM KKLOM PGIIK HYSUR YAQMV HSHLT KOXSU BYEDX FJPAY YJIUS PSPGI IKODF JXSJW TLASW FXRMN XFJCM YRGBZ PVKMN EXYXF JWSBI QYRRN OGQCE NICWW SBCMZ PSEGY SISKW RNKFI XFJWM BIQNE GOCMZ IXKWR JJEBI QTGIM YJNRV DLYYP SETPJ WIBGM TBINJ MTUEX HRMVR ISSBZ PVLYA VEFIP DXSYH ZWVEU JYXKH YRRUC IKWCI FRDFC LXINX FJKMX AMTUQ KRGXY SEPBH VVDEG SCCGI CUZJI SSPZP VIBFG SYVBJ VVKRB YYIXQ WORAC AMZCH BYQYR KKMLG LXDLC QZSXA CSKEG EWNEX YXFJW SBIQY RRNJM ZEHRM QTNRC YNUVV KRBSF SXICA VVURC BNLKX GYNEC JMWYI NMBSK QORRN FRSXY SUXRI QHRVO GPTNJ YYLIR XBICK LPVSD SLXCE LIWMV PCIUS BSRMP WLEQP VXGMR MKLOQ QTKLK XQMVA YYJIE SDFCM LRQVW KFVKP MSXXS QCXYI DLMZX LDXFN JAKWT JICUM LIRRN XFTLK RXDZC SPXFJ JGKVC HISGF SYJLO PYZXL OHFJR VDMJD RXDLC FNOGE PINEI MLBYM MLRMV TYSPH IIKXS WVTSG IJUYZ XFJEY DWFNJ TKHBJ ULKRB XNIBI QTTPE QQDRR NXFJE YDWUJ IICSQ RRPVX FFKLO HPTGT OHYQD SCXYX DEXCY XYIZY RNEXR IZFJO OXZZK XRIQH RVOGP TNHSH LTKQS RBMFA VSLLZ XDSMP YMWXM KZPVX FJSEC OCYWS BMRJE ELPCI YMWXM PVIZE UFPJB SKYYI PMPJR WRIDJ RVOHY XGEBO KNXLD KCYZR DSFNJ WDVYB RRNFS WELSQ SUJSR IIJGX KKMTU HSWRF EGOEU FPJBS KYYIP PYRVW KRBTE PIGYR VROEP YFGYZ CWUSB SRMPA SXFII CVIYA VWGLC SJLOP YDUSG RRTJP OINYY ICIIJ GXRIP AVVIW LZXEX HUFIQ KRBXY ICPCU KWYYL ICCER RNCQY VLNEK GLCSZ XGEQI RCVME MKXRI ENIPL ERMVH RIPKR GOMLF CMDXJ JIMZT JNEKL VMTBE XHQTF RKJRJ IXRIW FCPCX YWKIN XMBRV NXFJV QOVYQ UGSXW YYMCA YXKSL IYSVZ ORRKL PNEWK FVDLC YIEFI JJIWD LCDYE NLYWU PIFCJ EAKPI NEKKR FTLVG LCSKL OCQFN FOJMW VXRIK FXVOE RIZXM LRMRX MVMXJ INXFJ ISKHY SUHSZ GIVHD LCKFV OWRFJ JKVYX KLOCA TLPNW CJFRO MRMVV CMBJZ XGEQF MIBCU NUINM RHYEX HUMVR DLCDT VOTRZ GXYXF JVHQI YSUPY SIJUM XXMNK XRIWH FYVHQ JVMDA YXRPC STJIC NICUR RNXFJ IIGIP JDEXC ZNXNK KEJUV YGIXR XDLCG FXDSK YYICM BJJAO VCXFW DICUK LKXLT EIYJR MVQMS SQUGV MKGUS GRYSU JYVYR FQORR NKWOI KJUXR ERYYI SVHTL VXIWR LWDIL INLKX QMRPV ACIFE COCIU SBSRM PHOWN FZVSR EQPMR ETJEX DLCKR MXXCX KMNIY XRMNX FJKMX AMTUQ KRYSU XRIJN FRCLM TBLSW QMRKQ CKFEI KRBQF SUIBY YSEKF YWYVF SYKLO WAFII MVMBJ ESHUJ TEXRM YWPIX FFKMC GCWKE SRLJZ XRIPH RRGIA QZQLH MBEMX XMYYM CKPJR XNMRH YXRIP JWSBI GKNIM ELSFX TYKUF ZOVGY NIWYQ YJXYT UMVVO ACFII SXFNE OSGMZ CHTYK UFZOV GYJES HRMVG YAYWU PIPGT EEPXC WDIKW SWZRQ XFJUM CXYST IMEPJ WYVPW NELSW KNEHD LCSNI KVCFC PBMEM KEXWU JIINX FJJGK VCHIS GJMWP SEGYS TEBVW ZJEVP MAVVY RWTLV LEAPF ROERF KMWIU JCPSP JYICS XQFZH DLCQZ SXAFT NMVPE TWMBW RNNMV PBJTP KVCIK LOWAF IIMVM BWSBM DDFYP SSSUX RERDF YMSSQ URYXH ZDTYZ CWKLO KSQWH YVMYY CGSSQ UFOOG QCINS PYYID MLBFS NQYSS ENPWI VRDIB TEXRI PTTOC FCQFA LYRNW MKQMS PSEVZ FTOSX UNCPX SRRRX DIPXF QEGFK FVDLC KRPVA MZCHX SRMLV DQCFK EVP
krypton4@krypton:/krypton/krypton4$ cat krypton5 
HCIKV RJOX
krypton4@krypton:/krypton/krypton4$ exit
logout
Connection to krypton.labs.overthewire.org closed.
```

go to the website `https://www.dcode.fr/vigenere-cipher`
ciphertext of found1:
```
YYICS JIZIB AGYYX RIEWV IXAFN JOOVQ QVHDL CRKLB SSLYX RIQYI IOXQT WXRIC RVVKP BHZXI YLYZP DLCDI IKGFJ UXRIP TFQGL CWVXR IEZRV NMYSF JDLCL RXOWJ NMINX FNJSP JGHVV ERJTT OOHRM VMBWN JTXKG JJJXY TSYKL OQZFT OSRFN JKBIY YSSHE LIKLO RFJGS VMRJC CYTCS VHDLC LRXOJ MWFYB JPNVR NWUMZ GRVMF UPOEB XKSDL CBZGU IBBZX MLMKK LOACX KECOC IUSBS RMPXR IPJZW XSPTR HKRQB VVOHR MVKEE PIZEX SDYYI QERJJ RYSLJ VZOVU NJLOW RTXSD LYYNE ILMBK LORYW VAOXM KZRNL CWZRA YGWVH DLCLZ VVXFF KASPJ GVIKW WWVTV MCIKL OQYSW SBAFJ EWRII SFACC MZRVO MLYYI MSSSK VISDY YIGML PZICW FJNMV PDNEH ISSFE HWEIJ PSEEJ QYIBW JFMIC TCWYE ZWLTK WKMBY YICGY WVGBS UKFVG IKJRR DSBJJ XBSWM VVYLR MRXSW BNWJO VCSKW KMBYY IQYYW UMKRM KKLOK YYVWX SMSVL KWCAV VNIQY ISIIB MVVLI DTIIC SGSRX EVYQC CDLMZ XLDWF JNSEP BRROO WJFMI CSDDF YKWQM VLKWM KKLOV CXKFE XRFBI MEPJW SBWFJ ZWGMA PVHKR BKZIB GCFEH WEWSF XKPJT NCYYR TUICX PTPLO VIJVT DSRMV AOWRB YIBIR MVWER QJKWK RBDFY MELSF XPEGQ KSPML IYIBX FJPXR ELPVH RMKFE HLEBJ YMWKM TUFII YSUXE VLJUX YAYWU XRIUJ JXGEJ PZRQS TJIJS IJIJS PWMKK KBEQX USDXC IYIBI YSUXR IPJNM DLBFZ WSIQF EHLYR YVVMY NXUSB SRMPW DMJQN SBIRM VTBIR YPWSP IIIIC WQMVL KHNZK SXMLY YIZEJ FTILY RSFAD SFJIW EVNWZ WOWFJ WSERB NKAKW LTCSX KCWXV OILGL XZYPJ NLSXC YYIBM ZGFRK VMZEH DSRTJ ROGIM RHKPQ TCSCX GYJKB ICSTS VSPFE HGEQF JARMR JRWNS PTKLI WBWVW CXFJV QOVYQ UGSXW BRWCS MSCIP XDFIF OLGSU ECXFJ PENZY STINX FJXVY YLISI MEKJI SEKFJ IEXHF NCPSI PKFVD LCWVA OVCSF JKVKX ESBLM ZJICM LYYMC GMZEX BCMKK LOACX KEXHR MVKBS SSUAK WSSKM VPCIZ RDLCF WXOVL TFRDL CXLRC LMSVL YXGSK LOMPK RGOWD TIXRI PJNIB ILTKV OIQYF SPJCW KLOQQ MRHOW MYYED FCKFV ORGLY XNSPT KLIEL IKSDS YSUXR IJNFR GIPJK MBIBF EHVEW IFAXY NTEXR IEWRW CELIW IVPYX CIOTU NKLDL CBFSN QYSRR NXFJJ GKVCH ISGOC JGMXK UFKGR
```

plaintext of found1:
```
THESO LDIER WITHT HEGRE ENWHI SKERS LEDTH EMTHR OUGHT HESTR EETSO FTHEE MERAL DCITY UNTIL THEYR EACHE DTHER OOMWH ERETH EGUAR DIANO FTHEG ATESL IVEDT HISOF FICER UNLOC KEDTH EIRSP ECTAC LESTO PUTTH EMBAC KINHI SGREA TBOXA NDTHE NHEPO LITEL YOPEN EDTHE GATEF OROUR FRIEN DSWHI CHROA DLEAD STOTH EWICK EDWIT CHOFT HEWES TASKE DDORO THYTH EREIS NOROA DANSW EREDT HEGUA RDIAN OFTHE GATES NOONE EVERW ISHES TOGOT HATWA YHOWT HENAR EWETO FINDH ERINQ UIRED THEGI RLTHA TWILL BEEAS YREPL IEDTH EMANF ORWHE NSHEK NOWSY OUARE INTHE COUNT RYOFT HEWIN KIESS HEWIL LFIND YOUAN DMAKE YOUAL LHERS LAVES PERHA PSNOT SAIDT HESCA RECRO WFORW EMEAN TODES TROYH EROHT HATIS DIFFE RENTS AIDTH EGUAR DIANO FTHEG ATESN OONEH ASEVE RDEST ROYED HERBE FORES OINAT URALL YTHOU GHTSH EWOUL DMAKE SLAVE SOFYO UASSH EHASO FTHER ESTBU TTAKE CAREF ORSHE ISWIC KEDAN DFIER CEAND MAYNO TALLO WYOUT ODEST ROYHE RKEEP TOTHE WESTW HERET HESUN SETSA NDYOU CANNO TFAIL TOFIN DHERT HEYTH ANKED HIMAN DBADE HIMGO ODBYE ANDTU RNEDT OWARD THEWE STWAL KINGO VERFI ELDSO FSOFT GRASS DOTTE DHERE ANDTH EREWI THDAI SIESA NDBUT TERCU PSDOR OTHYS TILLW ORETH EPRET TYSIL KDRES SSHEH ADPUT ONINT HEPAL ACEBU TNOWT OHERS URPRI SESHE FOUND ITWAS NOLON GERGR EENBU TPURE WHITE THERI BBONA ROUND TOTOS NECKH ADALS OLOST ITSGR EENCO LORAN DWASA SWHIT EASDO ROTHY SDRES STHEE MERAL DCITY WASSO ONLEF TFARB EHIND ASTHE YADVA NCEDT HEGRO UNDBE CAMER OUGHE RANDH ILLIE RFORT HEREW ERENO FARMS NORHO USESI NTHIS COUNT RYOFT HEWES TANDT HEGRO UNDWA SUNTI LLEDI NTHEA FTERN OONTH ESUNS HONEH OTINT HEIRF ACESF ORTHE REWER ENOTR EESTO OFFER THEMS HADES OTHAT BEFOR ENIGH TDORO THYAN DTOTO ANDTH ELION WERET IREDA NDLAY DOWNU PONTH EGRAS SANDF ELLAS LEEPW ITHTH EWOOD MANAN DTHES CAREC ROWKE EPING WATCH
```

ciphertext of found2:
```
YYIIA CWVSL PGLVH DSAFD TYYRY YEDRG LYXER BJIEV EPLVX BICNE XRIDT IICXD TIXRI PJNIB ILTYS EWCXE IKVRM VXBIC RRHOE ETFHD LGHBG YZCWZ RQXMU ISDIA YKLOQ DWFQD LCIVA KRBYY IDMLB FSNQY STLYT NJUEQ VCFKT SPCTW AYSBB ZXRLG XRBOE LIUSB SRMPF EMJYR WZPCS UMNJG WVXRE RBRVW IBMVV KRBRR HOLCW WIOPJ JJWVS LJCCC LCFEH DSRTR XOXFJ CECXM KKLOM PGIIK HYSUR YAQMV HSHLT KOXSU BYEDX FJPAY YJIUS PSPGI IKODF JXSJW TLASW FXRMN XFJCM YRGBZ PVKMN EXYXF JWSBI QYRRN OGQCE NICWW SBCMZ PSEGY SISKW RNKFI XFJWM BIQNE GOCMZ IXKWR JJEBI QTGIM YJNRV DLYYP SETPJ WIBGM TBINJ MTUEX HRMVR ISSBZ PVLYA VEFIP DXSYH ZWVEU JYXKH YRRUC IKWCI FRDFC LXINX FJKMX AMTUQ KRGXY SEPBH VVDEG SCCGI CUZJI SSPZP VIBFG SYVBJ VVKRB YYIXQ WORAC AMZCH BYQYR KKMLG LXDLC QZSXA CSKEG EWNEX YXFJW SBIQY RRNJM ZEHRM QTNRC YNUVV KRBSF SXICA VVURC BNLKX GYNEC JMWYI NMBSK QORRN FRSXY SUXRI QHRVO GPTNJ YYLIR XBICK LPVSD SLXCE LIWMV PCIUS BSRMP WLEQP VXGMR MKLOQ QTKLK XQMVA YYJIE SDFCM LRQVW KFVKP MSXXS QCXYI DLMZX LDXFN JAKWT JICUM LIRRN XFTLK RXDZC SPXFJ JGKVC HISGF SYJLO PYZXL OHFJR VDMJD RXDLC FNOGE PINEI MLBYM MLRMV TYSPH IIKXS WVTSG IJUYZ XFJEY DWFNJ TKHBJ ULKRB XNIBI QTTPE QQDRR NXFJE YDWUJ IICSQ RRPVX FFKLO HPTGT OHYQD SCXYX DEXCY XYIZY RNEXR IZFJO OXZZK XRIQH RVOGP TNHSH LTKQS RBMFA VSLLZ XDSMP YMWXM KZPVX FJSEC OCYWS BMRJE ELPCI YMWXM PVIZE UFPJB SKYYI PMPJR WRIDJ RVOHY XGEBO KNXLD KCYZR DSFNJ WDVYB RRNFS WELSQ SUJSR IIJGX KKMTU HSWRF EGOEU FPJBS KYYIP PYRVW KRBTE PIGYR VROEP YFGYZ CWUSB SRMPA SXFII CVIYA VWGLC SJLOP YDUSG RRTJP OINYY ICIIJ GXRIP AVVIW LZXEX HUFIQ KRBXY ICPCU KWYYL ICCER RNCQY VLNEK GLCSZ XGEQI RCVME MKXRI ENIPL ERMVH RIPKR GOMLF CMDXJ JIMZT JNEKL VMTBE XHQTF RKJRJ IXRIW FCPCX YWKIN XMBRV NXFJV QOVYQ UGSXW YYMCA YXKSL IYSVZ ORRKL PNEWK FVDLC YIEFI JJIWD LCDYE NLYWU PIFCJ EAKPI NEKKR FTLVG LCSKL OCQFN FOJMW VXRIK FXVOE RIZXM LRMRX MVMXJ INXFJ ISKHY SUHSZ GIVHD LCKFV OWRFJ JKVYX KLOCA TLPNW CJFRO MRMVV CMBJZ XGEQF MIBCU NUINM RHYEX HUMVR DLCDT VOTRZ GXYXF JVHQI YSUPY SIJUM XXMNK XRIWH FYVHQ JVMDA YXRPC STJIC NICUR RNXFJ IIGIP JDEXC ZNXNK KEJUV YGIXR XDLCG FXDSK YYICM BJJAO VCXFW DICUK LKXLT EIYJR MVQMS SQUGV MKGUS GRYSU JYVYR FQORR NKWOI KJUXR ERYYI SVHTL VXIWR LWDIL INLKX QMRPV ACIFE COCIU SBSRM PHOWN FZVSR EQPMR ETJEX DLCKR MXXCX KMNIY XRMNX FJKMX AMTUQ KRYSU XRIJN FRCLM TBLSW QMRKQ CKFEI KRBQF SUIBY YSEKF YWYVF SYKLO WAFII MVMBJ ESHUJ TEXRM YWPIX FFKMC GCWKE SRLJZ XRIPH RRGIA QZQLH MBEMX XMYYM CKPJR XNMRH YXRIP JWSBI GKNIM ELSFX TYKUF ZOVGY NIWYQ YJXYT UMVVO ACFII SXFNE OSGMZ CHTYK UFZOV GYJES HRMVG YAYWU PIPGT EEPXC WDIKW SWZRQ XFJUM CXYST IMEPJ WYVPW NELSW KNEHD LCSNI KVCFC PBMEM KEXWU JIINX FJJGK VCHIS GJMWP SEGYS TEBVW ZJEVP MAVVY RWTLV LEAPF ROERF KMWIU JCPSP JYICS XQFZH DLCQZ SXAFT NMVPE TWMBW RNNMV PBJTP KVCIK LOWAF IIMVM BWSBM DDFYP SSSUX RERDF YMSSQ URYXH ZDTYZ CWKLO KSQWH YVMYY CGSSQ UFOOG QCINS PYYID MLBFS NQYSS ENPWI VRDIB TEXRI PTTOC FCQFA LYRNW MKQMS PSEVZ FTOSX UNCPX SRRRX DIPXF QEGFK FVDLC KRPVA MZCHX SRMLV DQCFK EVP
```

plaintext of found2:
```
THEYW EREOB LIGED TOCAM POUTT HATNI GHTUN DERAL ARGET REEIN THEFO RESTF ORTHE REWER ENOHO USESN EARTH ETREE MADEA GOODT HICKC OVERI NGTOP ROTEC TTHEM FROMT HEDEW ANDTH ETINW OODMA NCHOP PEDAG REATP ILEOF WOODW ITHHI SAXEA NDDOR OTHYB UILTA SPLEN DIDFI RETHA TWARM EDHER ANDMA DEHER FEELL ESSLO NELYS HEAND TOTOA TETHE LASTO FTHEI RBREA DANDN OWSHE DIDNO TKNOW WHATT HEYWO ULDDO FORBR EAKFA STIFY OUWIS HSAID THELI ONIWI LLGOI NTOTH EFORE STAND KILLA DEERF ORYOU YOUCA NROAS TITBY THEFI RESIN CEYOU RTAST ESARE SOPEC ULIAR THATY OUPRE FERCO OKEDF OODAN DTHEN YOUWI LLHAV EAVER YGOOD BREAK FASTD ONTPL EASED ONTBE GGEDT HETIN WOODM ANISH OULDC ERTAI NLYWE EPIFY OUKIL LEDAP OORDE ERAND THENM YJAWS WOULD RUSTA GAINB UTTHE LIONW ENTAW AYINT OTHEF OREST ANDFO UNDHI SOWNS UPPER ANDNO ONEEV ERKNE WWHAT ITWAS FORHE DIDNT MENTI ONITA NDTHE SCARE CROWF OUNDA TREEF ULLOF NUTSA NDFIL LEDDO ROTHY SBASK ETWIT HTHEM SOTHA TSHEW OULDN OTBEH UNGRY FORAL ONGTI MESHE THOUG HTTHI SWASV ERYKI NDAND THOUG HTFUL OFTHE SCARE CROWB UTSHE LAUGH EDHEA RTILY ATTHE AWKWA RDWAY INWHI CHTHE POORC REATU REPIC KEDUP THENU TSHIS PADDE DHAND SWERE SOCLU MSYAN DTHEN UTSWE RESOS MALLT HATHE DROPP EDALM OSTAS MANYA SHEPU TINTH EBASK ETBUT THESC ARECR OWDID NOTMI NDHOW LONGI TTOOK HIMTO FILLT HEBAS KETFO RITEN ABLED HIMTO KEEPA WAYFR OMTHE FIREA SHEFE AREDA SPARK MIGHT GETIN TOHIS STRAW ANDBU RNHIM UPSOH EKEPT AGOOD DISTA NCEAW AYFRO MTHEF LAMES ANDON LYCAM ENEAR TOCOV ERDOR OTHYW ITHDR YLEAV ESWHE NSHEL AYDOW NTOSL EEPTH ESEKE PTHER VERYS NUGAN DWARM ANDSH ESLEP TSOUN DLYUN TILMO RNING WHENI TWASD AYLIG HTTHE GIRLB ATHED HERFA CEINA LITTL ERIPP LINGB ROOKA NDSOO NAFTE RTHEY ALLST ARTED TOWAR DTHEE MERAL DCITY THISW ASTOB EANEV ENTFU LDAYF ORTHE TRAVE LERST HEYHA DHARD LYBEE NWALK INGAN HOURW HENTH EYSAW BEFOR ETHEM AGREA TDITC HTHAT CROSS EDTHE ROADA NDDIV IDEDT HEFOR ESTAS FARAS THEYC OULDS EEONE ITHER SIDEI TWASA VERYW IDEDI TCHAN DWHEN THEYC REPTU PTOTH EEDGE ANDLO OKEDI NTOIT THEYC OULDS EEITW ASALS OVERY DEEPA NDTHE REWER EMANY BIGJA GGEDR OCKSA TTHEB OTTOM THESI DESWE RESOS TEEPT HATNO NEOFT HEMCO ULDCL IMBDO WNAND FORAM OMENT ITSEE MEDTH ATTHE IRJOU RNEYM USTEN DWHAT SHALL WEDOA SKEDD OROTH YDESP AIRIN GLYIH AVENT THEFA INTES TIDEA SAIDT HETIN WOODM ANAND THELI ONSHO OKHIS SHAGG YMANE ANDLO OKEDT HOUGH TFULB UTTHE SCARE CROWS AIDWE CANNO TFLYT HATIS CERTA INNEI THERC ANWEC LIMBD OWNIN TOTHI SGREA TDITC HTHER EFORE IFWEC ANNOT JUMPO VERIT WEMUS TSTOP WHERE WEARE ITHIN KICOU LDJUM POVER ITSAI DTHEC OWARD LYLIO NAFTE RMEAS URING THEDI STANC ECARE FULLY INHIS MINDT HENWE AREAL LRIGH TANSW EREDT HESCA RECRO WFORY OUCAN CARRY USALL OVERO NYOUR BACKO NEATA TIMEW ELLIL LTRYI TSAID THELI ONWHO WILLG OFIRS TIWIL LDECL AREDT HESCA RECRO WFORI FYOUF OUNDT HATYO UCOUL DNOTJ UMPOV ERTHE GULFD OROTH YWOUL DBEKI LLEDO RTHET INWOO DMANB ADLYD ENTED ONTHE ROCKS BELOW BUTIF IAMON YOURB ACKIT WILLN OTMAT TERSO MUCHF ORTHE FALLW OULDN OTHUR TMEAT ALL
```

ciphertext of krypton5: 
```
HCIKV RJOX
```

plaintext of krypton5: 
```
CLEAR TEXT
```

key found: `FREKEY`

password is `CLEARTEXT` for next level

<br><br><br><br><br>






## Krypton 5
### Level Info
FA can break a known key length as well. Lets try one last polyalphabetic cipher, but this time the key length is unknown. Note: the text is writen in American English

Enjoy.

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton5@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
krypton5@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton5@krypton:~$ cd /krypton/
krypton5@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton5@krypton:/krypton$ cd krypton5
krypton5@krypton:/krypton/krypton5$ ls
found1  found2  found3  krypton6  README
krypton5@krypton:/krypton/krypton5$ cat README 
Frequency analysis can break a known key length as well.  Lets try one
last polyalphabetic cipher, but this time the key length is unknown.


Enjoy.


krypton5@krypton:/krypton/krypton5$ cat found1
SXULW GNXIO WRZJG OFLCM RHEFZ ALGSP DXBLM PWIQT XJGLA RIYRI BLPPC HMXMG CTZDL CLKRU YMYSJ TWUTX ZCMRH EFZAL OTMNL BLULV MCQMG CTZDL CPTBI AVPML NVRJN SSXWT XJGLA RIQPE FUGVP PGRLG OMDKW RSIFK TZYRM QHNXD UOWQT XJGLA RIQAV VTZVP LMAIV ZPHCX FPAVT MLBSD OIFVT PBACS EQKOL BCRSM AMULP SPPYF CXOKH LZXUO GNLID ZVRAL DOACC INREN YMLRH VXXJD XMSIN BXUGI UPVRG ESQSG YKQOK LMXRS IBZAL BAYJM AYAVB XRSIC KKPYH ULWFU YHBPG VIGNX WBIQP RGVXY SSBEL NZLVW IMQMG YGVSW GPWGG NARSP TXVKL PXWGD XRJHU SXQMI VTZYO GCTZR JYVBK MZHBX YVBIT TPVTM OOWSA IERTA SZCOI TXXLY JAZQC GKPCS LZRYE MOOVC HIEKT RSREH MGNTS KVEPN NCTUN EOFIR TPPDL YAPNO GMKGC ZRGNX ARVMY IBLXU QPYYH GNXYO ACCIN QBUQA GELNR TYQIH LANTW HAYCP RJOMO KJYTV SGVLY RRSIG NKVXI MQJEG GJOML MSGNV VERRC MRYBA GEQNP RGKLB XFLRP XRZDE JESGN XSYVB DSSZA LCXYE ICXXZ OVTPW BLEVK ZCDEA JYPCL CDXUG MARML RWVTZ LXIPL PJKKL CIREP RJYVB ITPVV ZPHCX FPCRG KVPSS CPBXW VXIRS SHYTU NWCGI ANNUN VCOEA JLLFI LECSO OLCTG CMGAT SBITP PNZBV XWUPV RIHUM IBPHG UXUQP YYHNZ MOKXD LZBAK LNTCC MBJTZ KXRSM FSKZC SSELP UMARE BCIPK GAVCY EXNOG LNLCC JVBXH XHRHI AZBLD LZWIF YXKLM PELQG RVPAF ZQNVK VZLCE MPVKP FERPM AZALV MDPKH GKKCL YOLRX TSNIB ELRYN IVMKP ECVXH BELNI OETUX SSYGV TZARE RLVEG GNOQC YXFCX YOQYO ISUKA RIQHE YRHDS REFTB LEVXH MYEAJ PLCXK TRFZX YOZCY XUKVV MOJLR RMAVC XFLHO KXUVE GOSAR RHBSS YHQUS LXSDJ INXLH PXCCV NVIPX KMFXV ZLTOW QLKRY TZDLC DTVXB ACSDE LVYOL BCWPE ERTZD TYDXF AILBR YEYEG ESIHC QMPOX UDMLZ VVMBU KPGEC EGIWO HMFXG NXPBW KPVRS XZCEE PWVTM OOIYC XURRV BHCCS SKOLX XQSEQ RTAOP WNSZK MVDLC PRTRB ZRGPZ AAGGK ZIMAP RLKVW EAZRT XXZCS DMVVZ BZRWS MNRIM ZSRYX IEOVH GLGNL FZKHX KCESE KEHDI FLZRV KVFIB XSEKB TZSPE EAZMV DLCSY ZGGYK GCELN TTUIG MXQHT BJKXG ZRFEX ABIAP MIKWA RVMFK UGGFY JRSIP NBJUI LDSSZ ALMSA VPNTX IBSMO
krypton5@krypton:/krypton/krypton5$ cat found2
GLCYX UKFHS PEZXF AVJOW QQYYR RAYHM GIEOG ARIAZ YEYXV PXFPJ BXXUY SLELR NXHNH PLARX TADLC CSLGE NOSPR IUUML VSNPR RJMOO GMLGU JHVBE QSMFI NZDSK HEFNX KSHGE AVZAZ YQCQP BAKPC LMQGR XXTYR WQSEG FHSPH ZYETX FPVMX PBTWV XMLHM AZXYG EQLRN IAPOZ CXIAZ MVMSL RVNZN SKXCL RNJOL XXSCS HYMYK ZCWPR XNWYR ZJXUG MASQC ELRXX DKWMY PLUGL KHTPR GAKVE WRCEI KESOV JPJGH XJYRE CEGAE HDIBQ SEZAL DAMZX UKKZR EBMIR TLLDH MHRNZ MOOMP CIFVX JDMTP VBGWZ SHCOI FZBUK XGZRF ZALWM JOIJE BUCMB PSSZA LMSYN LJOMO SXQOE ZVTUN HGCXL YMYKA GEWQO LHQIC LFYKL TOPJL RQOMZ YFQNY EOMFG EQCEG NXYVM IPEYG KNOVB ZKXKG UOPKC PBXKF DLCAE FYXUQ IPDLN QBUQL GXWRR YVEXM QMGOG JREGY WBLLA BEULX NTZSO SDDLN MZFGV YATRX YSKTN TRTNT AKRBX YQJRS OKQHE FXTAR IPWMX KTSKV EPVFU KAYJB ZKGNX YOAGW POKTW KGIPX GUVHV EGDXB SHYBS UOVNC XYIIQ DMEOY ARIUP EGNXY RSJOW NTWAR IUTRQ YXACX MWIEG USOJY TVGNX ASHCH MYRLL BZCAV RZMFX MAPPL GMHLS SEXJU BUDLC LJGKK UYSLD MEHXK CMPTW UGESX SRRSG UULNX GWPAO ZODFS EMJGG AKFCO VBUFH XHYME EHXYK RBELR TUYOE IQEFZ LPBCC DWVXM OKXUL CFOKP PCMFT YKTZO WFZAP UGJYV BRIAZ ELWEL DZNRB ZOELO LBZPH DIPES PUGJY VBAYY RHMPK CYXYK FHXWZ ZSGYB UMSLN SEJRV EAGWP SOGKK JGYIF KTJYE JQMEK LPBJC EGUHT YLIPE SPUGJ YVBDX VXTIY YRELR XXUYA DZVPU GJYVB ELRIH UMSPO FRJVO KQZPV OKBUQ EJHEL YTZCM EYIQZ HHZEQ DIAMX YLCRS IZGBS KRBAE FYXUQ IPDFL ZALWE GWFRO GNKPU LCFNX HFMJJ AEGIW OHSAJ EUFOO EBESS UHADL CCSBS AHNXF PSQJB UDIPP WGLHY DLCPW GGUSS WFXIA ZHMDL CCSLG ENOSP RIGNT AKPRS SHMAI EXMYI XOGKY JKLRJ GLZOI LESTU BUDSG EEYRD PXHQL RQBTY SIRTI FUYTO RALQR UNAYJ GEGBT LLAYC YXYET UYXFP VQXTD OVYYH GCHWY VRPVF GGKCI TPVNR FHSHQ LRQZA LVELO PNJRD OVCLP YRHPD IPTRT HRHMG GOIAZ TAFEP TSHYI VSRRD SSZAL BSYOF RZPLO RRSIP UGJYV BLRQZ ALMSD QIRXH VWAFP RNMXU DPCXE AUYZS BRJJB XFHVP WOVRY LLNML LFEUP UCYGE SSIEV DLCDT EKMAI ACWPJ UKULY RGIEE PLVPI PTGCB ARPYC KRYJB KVCNY SLLHX HJLVT KYSKT QESGN XWYGI PXFVT ZCIBL PBTZV XLGDA NEMVR MQMVR GDMKW R
krypton5@krypton:/krypton/krypton5$ cat found3
FIPJS EJXYV CYYHZ KMOYH GNEYN XSYSI PHJOM OKLYY HBTXH MLIYI RGGKK PMFHJ GMJRX GNOVT ZHCSL ZVBAL ZOVKZ RHTWL BLGDJ YGIWO HULMF ZVVKX YDXUU NNRMR AMGZX KSXQR VNBBA IELOP BTZLF MRJET GBUCX RSIYK OPDCY YHRBT UOWAP RPKHM DLCMV VYDMS VCSIU GWHQS MOPRM TUNAY DEYOM AVITL MAUYP DJMCL VYUYY ALDXB IDPXK QQMGZ XKCPC PONTW JVSQP EAJPL BIMQE SOGLD IVEYE KAPCW FZIFG GKLYA VPRYM VYXFZ YTNIS KMLHI EKMYS QFPAB XXHXS BOPVZ MSOWJ PIXIK PCTDW EKKGD SKQPX GOGNF IPJGY ULLDS FTWUK TKGLG NLJOZ PDMQE SOKIY OWSXI QCTZW EBPSS NTPBF SEAUO VOVSM VIQLT YWSPP EFZAV EKFTX JKKLC TSYJE UFMSP YXIAZ LVPWG WOBXZ SKWQS MFRBU ORRSS HMAUY XMQES OGLXI QDMAG VJYVB LRPKP PDLFT WFZHJ UMLRW JGLHC AFTXR GLARI RZTFU YARIU LZRYM OKXZC SXKNW YRRSI AKBNR FMFVV TZIOE ASSEZ ALCTC NOFUY ZKMJE LNZZS SRRPH VTMOO WSYPV MAAPE PLXFK THPEA PLNHB AEEJW CFAIW BIQDI QGGKA YGPXR JPHCW RTPYR BNRXC OYCAG KOVRS IDATP XXUTK OETWK MPZJZ UBZDF PTKUZ XFOWR SEGOM TEWRS EIKVV CXRSI VXHDX IPTRL KTYCK MYIOE LVWIN LMAYM VNVGW PGUMO OGMXT BYXKK RBCIF KKCOH CITEK LZSSL ZJGKE SCSLD FNTDO OLYOE UKTSD LWNSY UNYSR FTWPN XLUWY YHUOL MKGCE LBAZO VMLPH OUKLP IUEVN IXZYJ YYBVK MFLYR AIENT WCXFP GBTYP NILEM NRUHM LCWSE IELBO QTRGK ESCSL DFNTD DOVCA VVTVP ZEJWC BIVBZ MCOAV ZAARI ALVRY HMYXF PVCKH WVIYY HCKKO KTQDI PUGKR ELOGN XXZVM IPWRI HUNLY YHPRH ARIQN SZKXH CMJJS SLTUN SLNSZ VELDM LRLVY KLCIK MPNTV LDSYX EACAV GEQDM GZBUQ JMCLV YIVBX PLMGS KSYVP JHEUI WOHMQ JGULS OINEL RGKYS ZYWSS NBZLV CLOSG LABSS DIQNB TKRBS IFGBK DSRSI QXTDO VYDLR SHCOH FTWPN TPBXM TXVCB ZREAN SZSHK KXGZR CXXWK VCOJB XTFYY LRPNJ RDRSK LCPUF LRIPP EGGGF DMKPX BJTFC LCXEL GLRPS PXVWG KCSWJ ZVEEH YCLCX ELUGS IEQVJ BXTNO RRWIZ GGMBS KEIYR LVXWZ LRXVE LKWCE SYKMT OOLZA LKLZS VRPPY YHUCF YYOVT EVXHM YWVXR LCCCD WVXPL RETPS SZXUD MKPWG NXOYR MFVGU XUDIP EEVTR VEVEP RGRXT ORGYX UKBYD VYGIY RBUQF YNOJG KKCEL OJBXP HBHQM IGCBE DPMYH BTTUN TYCMF YBYKZ YDXQK TSYJR CEIKE SSRED MEOGA OPJDS AGGKM SKAEA ELOYY QPCRY PLKVC BYVZX HPVCY GUNHB CIYDA RREHC ELPRT RBZRS LPCRY LPBRM EQHIA PXXFP LNHBA YJQFG UZKHF IJWMA MRVEV QPPSO MOSRI DMETH AYJJL XREXH BWGEM FLBMD ICYCR GKZCM LNIJK LPXGC TGNSX SKWRQ VBSYY KRAP
krypton5@krypton:/krypton/krypton5$ cat krypton6 
BELOS Z
krypton5@krypton:/krypton/krypton5$ exit
logout
Connection to krypton.labs.overthewire.org closed.
```

go to the website `https://www.dcode.fr/vigenere-cipher`
ciphertext of found1:
```
SXULW GNXIO WRZJG OFLCM RHEFZ ALGSP DXBLM PWIQT XJGLA RIYRI BLPPC HMXMG CTZDL CLKRU YMYSJ TWUTX ZCMRH EFZAL OTMNL BLULV MCQMG CTZDL CPTBI AVPML NVRJN SSXWT XJGLA RIQPE FUGVP PGRLG OMDKW RSIFK TZYRM QHNXD UOWQT XJGLA RIQAV VTZVP LMAIV ZPHCX FPAVT MLBSD OIFVT PBACS EQKOL BCRSM AMULP SPPYF CXOKH LZXUO GNLID ZVRAL DOACC INREN YMLRH VXXJD XMSIN BXUGI UPVRG ESQSG YKQOK LMXRS IBZAL BAYJM AYAVB XRSIC KKPYH ULWFU YHBPG VIGNX WBIQP RGVXY SSBEL NZLVW IMQMG YGVSW GPWGG NARSP TXVKL PXWGD XRJHU SXQMI VTZYO GCTZR JYVBK MZHBX YVBIT TPVTM OOWSA IERTA SZCOI TXXLY JAZQC GKPCS LZRYE MOOVC HIEKT RSREH MGNTS KVEPN NCTUN EOFIR TPPDL YAPNO GMKGC ZRGNX ARVMY IBLXU QPYYH GNXYO ACCIN QBUQA GELNR TYQIH LANTW HAYCP RJOMO KJYTV SGVLY RRSIG NKVXI MQJEG GJOML MSGNV VERRC MRYBA GEQNP RGKLB XFLRP XRZDE JESGN XSYVB DSSZA LCXYE ICXXZ OVTPW BLEVK ZCDEA JYPCL CDXUG MARML RWVTZ LXIPL PJKKL CIREP RJYVB ITPVV ZPHCX FPCRG KVPSS CPBXW VXIRS SHYTU NWCGI ANNUN VCOEA JLLFI LECSO OLCTG CMGAT SBITP PNZBV XWUPV RIHUM IBPHG UXUQP YYHNZ MOKXD LZBAK LNTCC MBJTZ KXRSM FSKZC SSELP UMARE BCIPK GAVCY EXNOG LNLCC JVBXH XHRHI AZBLD LZWIF YXKLM PELQG RVPAF ZQNVK VZLCE MPVKP FERPM AZALV MDPKH GKKCL YOLRX TSNIB ELRYN IVMKP ECVXH BELNI OETUX SSYGV TZARE RLVEG GNOQC YXFCX YOQYO ISUKA RIQHE YRHDS REFTB LEVXH MYEAJ PLCXK TRFZX YOZCY XUKVV MOJLR RMAVC XFLHO KXUVE GOSAR RHBSS YHQUS LXSDJ INXLH PXCCV NVIPX KMFXV ZLTOW QLKRY TZDLC DTVXB ACSDE LVYOL BCWPE ERTZD TYDXF AILBR YEYEG ESIHC QMPOX UDMLZ VVMBU KPGEC EGIWO HMFXG NXPBW KPVRS XZCEE PWVTM OOIYC XURRV BHCCS SKOLX XQSEQ RTAOP WNSZK MVDLC PRTRB ZRGPZ AAGGK ZIMAP RLKVW EAZRT XXZCS DMVVZ BZRWS MNRIM ZSRYX IEOVH GLGNL FZKHX KCESE KEHDI FLZRV KVFIB XSEKB TZSPE EAZMV DLCSY ZGGYK GCELN TTUIG MXQHT BJKXG ZRFEX ABIAP MIKWA RVMFK UGGFY JRSIP NBJUI LDSSZ ALMSA VPNTX IBSMO
```
plaintext of found1:
```
ITWAS THEBE STOFT IMESI TWAST HEWOR STOFT IMESI TWAST HEAGE OFWIS DOMIT WASTH EAGEO FFOOL ISHNE SSITW ASTHE EPOCH OFBEL IEFIT WASTH EEPOC HOFIN CREDU LITYI TWAST HESEA SONOF LIGHT ITWAS THESE ASONO FDARK NESSI TWAST HESPR INGOF HOPEI TWAST HEWIN TEROF DESPA IRWEH ADEVE RYTHI NGBEF OREUS WEHAD NOTHI NGBEF OREUS WEWER EALLG OINGD IRECT TOHEA VENWE WEREA LLGOI NGDIR ECTTH EOTHE RWAYI NSHOR TTHEP ERIOD WASSO FARLI KETHE PRESE NTPER IODTH ATSOM EOFIT SNOIS IESTA UTHOR ITIES INSIS TEDON ITSBE INGRE CEIVE DFORG OODOR FOREV ILINT HESUP ERLAT IVEDE GREEO FCOMP ARISO NONLY THERE WEREA KINGW ITHAL ARGEJ AWAND AQUEE NWITH APLAI NFACE ONTHE THRON EOFEN GLAND THERE WEREA KINGW ITHAL ARGEJ AWAND AQUEE NWITH AFAIR FACEO NTHET HRONE OFFRA NCEIN BOTHC OUNTR IESIT WASCL EARER THANC RYSTA LTOTH ELORD SOFTH ESTAT EPRES ERVES OFLOA VESAN DFISH ESTHA TTHIN GSING ENERA LWERE SETTL EDFOR EVERI TWAST HEYEA ROFOU RLORD ONETH OUSAN DSEVE NHUND REDAN DSEVE NTYFI VESPI RITUA LREVE LATIO NSWER ECONC EDEDT OENGL ANDAT THATF AVOUR EDPER IODAS ATTHI SMRSS OUTHC OTTHA DRECE NTLYA TTAIN EDHER FIVEA NDTWE NTIET HBLES SEDBI RTHDA YOFWH OMAPR OPHET ICPRI VATEI NTHEL IFEGU ARDSH ADHER ALDED THESU BLIME APPEA RANCE BYANN OUNCI NGTHA TARRA NGEME NTSWE REMAD EFORT HESWA LLOWI NGUPO FLOND ONAND WESTM INSTE REVEN THECO CKLAN EGHOS THADB EENLA IDONL YAROU NDDOZ ENOFY EARSA FTERR APPIN GOUTI TSMES SAGES ASTHE SPIRI TSOFT HISVE RYYEA RLAST PASTS UPERN ATURA LLYDE FICIE NTINO RIGIN ALITY RAPPE DOUTT HEIRS MEREM ESSAG ESINT HEEAR THLYO RDERO FEVEN TSHAD LATEL YCOME TOTHE ENGLI SHCRO WNAND PEOPL EFROM ACONG RESSO FBRIT ISHSU BJECT SINAM ERICA WHICH STRAN GETOR ELATE HAVEP ROVED MOREI MPORT ANTTO THEHU MANRA CETHA NANYC OMMUN ICATI ONSYE TRECE IVEDT HROUG HANYO FTHEC HICKE NSOFT HECOC KLANE BROOD
```

ciphertext of found2:
```
GLCYX UKFHS PEZXF AVJOW QQYYR RAYHM GIEOG ARIAZ YEYXV PXFPJ BXXUY SLELR NXHNH PLARX TADLC CSLGE NOSPR IUUML VSNPR RJMOO GMLGU JHVBE QSMFI NZDSK HEFNX KSHGE AVZAZ YQCQP BAKPC LMQGR XXTYR WQSEG FHSPH ZYETX FPVMX PBTWV XMLHM AZXYG EQLRN IAPOZ CXIAZ MVMSL RVNZN SKXCL RNJOL XXSCS HYMYK ZCWPR XNWYR ZJXUG MASQC ELRXX DKWMY PLUGL KHTPR GAKVE WRCEI KESOV JPJGH XJYRE CEGAE HDIBQ SEZAL DAMZX UKKZR EBMIR TLLDH MHRNZ MOOMP CIFVX JDMTP VBGWZ SHCOI FZBUK XGZRF ZALWM JOIJE BUCMB PSSZA LMSYN LJOMO SXQOE ZVTUN HGCXL YMYKA GEWQO LHQIC LFYKL TOPJL RQOMZ YFQNY EOMFG EQCEG NXYVM IPEYG KNOVB ZKXKG UOPKC PBXKF DLCAE FYXUQ IPDLN QBUQL GXWRR YVEXM QMGOG JREGY WBLLA BEULX NTZSO SDDLN MZFGV YATRX YSKTN TRTNT AKRBX YQJRS OKQHE FXTAR IPWMX KTSKV EPVFU KAYJB ZKGNX YOAGW POKTW KGIPX GUVHV EGDXB SHYBS UOVNC XYIIQ DMEOY ARIUP EGNXY RSJOW NTWAR IUTRQ YXACX MWIEG USOJY TVGNX ASHCH MYRLL BZCAV RZMFX MAPPL GMHLS SEXJU BUDLC LJGKK UYSLD MEHXK CMPTW UGESX SRRSG UULNX GWPAO ZODFS EMJGG AKFCO VBUFH XHYME EHXYK RBELR TUYOE IQEFZ LPBCC DWVXM OKXUL CFOKP PCMFT YKTZO WFZAP UGJYV BRIAZ ELWEL DZNRB ZOELO LBZPH DIPES PUGJY VBAYY RHMPK CYXYK FHXWZ ZSGYB UMSLN SEJRV EAGWP SOGKK JGYIF KTJYE JQMEK LPBJC EGUHT YLIPE SPUGJ YVBDX VXTIY YRELR XXUYA DZVPU GJYVB ELRIH UMSPO FRJVO KQZPV OKBUQ EJHEL YTZCM EYIQZ HHZEQ DIAMX YLCRS IZGBS KRBAE FYXUQ IPDFL ZALWE GWFRO GNKPU LCFNX HFMJJ AEGIW OHSAJ EUFOO EBESS UHADL CCSBS AHNXF PSQJB UDIPP WGLHY DLCPW GGUSS WFXIA ZHMDL CCSLG ENOSP RIGNT AKPRS SHMAI EXMYI XOGKY JKLRJ GLZOI LESTU BUDSG EEYRD PXHQL RQBTY SIRTI FUYTO RALQR UNAYJ GEGBT LLAYC YXYET UYXFP VQXTD OVYYH GCHWY VRPVF GGKCI TPVNR FHSHQ LRQZA LVELO PNJRD OVCLP YRHPD IPTRT HRHMG GOIAZ TAFEP TSHYI VSRRD SSZAL BSYOF RZPLO RRSIP UGJYV BLRQZ ALMSD QIRXH VWAFP RNMXU DPCXE AUYZS BRJJB XFHVP WOVRY LLNML LFEUP UCYGE SSIEV DLCDT EKMAI ACWPJ UKULY RGIEE PLVPI PTGCB ARPYC KRYJB KVCNY SLLHX HJLVT KYSKT QESGN XWYGI PXFVT ZCIBL PBTZV XLGDA NEMVR MQMVR GDMKW R
```
plaintext of found2:
```
WHENT HEMAI LGOTS UCCES SFULL YTODO VERIN THECO URSEO FTHEF ORENO ONTHE HEADD RAWER ATTHE ROYAL GEORG EHOTE LOPEN EDTHE COACH DOORA SHISC USTOM WASHE DIDIT WITHS OMEFL OURIS HOFCE REMON YFORA MAILJ OURNE YFROM LONDO NINWI NTERW ASANA CHIEV EMENT TOCON GRATU LATEA NADVE NTURO USTRA VELLE RUPON BYTHA TTIME THERE WASON LYONE ADVEN TUROU STRAV ELLER LEFTB ECONG RATUL ATEDF ORTHE TWOOT HERSH ADBEE NSETD OWNAT THEIR RESPE CTIVE ROADS IDEDE STINA TIONS THEMI LDEWY INSID EOFTH ECOAC HWITH ITSDA MPAND DIRTY STRAW ITSDI SAGEE ABLES MELLA NDITS OBSCU RITYW ASRAT HERLI KEALA RGERD OGKEN NELMR LORRY THEPA SSENG ERSHA KINGH IMSEL FOUTO FITIN CHAIN SOFST RAWAT ANGLE OFSHA GGYWR APPER FLAPP INGHA TANDM UDDYL EGSWA SRATH ERLIK EALAR GERSO RTOFD OGTHE REWIL LBEAP ACKET TOCAL AISTO MORRO WDRAW ERYES SIRIF THEWE ATHER HOLDS ANDTH EWIND SETST OLERA BLEFA IRTHE TIDEW ILLSE RVEPR ETTYN ICELY ATABO UTTWO INTHE AFTER NOONS IRBED SIRIS HALLN OTGOT OBEDT ILLNI GHTBU TIWAN TABED ROOMA NDABA RBERA NDTHE NBREA KFAST SIRYE SSIRT HATWA YSIRI FYOUP LEASE SHOWC ONCOR DGENT LEMAN SVALI SEAND HOTWA TERTO CONCO RDPUL LOFFG ENTLE MANSB OOTSI NCONC ORDYO UWILL FINDA FINES EACOA LFIRE SIRFE TCHBA RBERT OCONC ORDST IRABO UTTHE RENOW FORCO NCORD THECO NCORD BEDCH AMBER BEING ALWAY SASSI GNEDT OAPAS SENGE RBYTH EMAIL ANDPA SSENG ERSBY THEMA ILBEI NGALW AYSHE AVILY WRAPP EDUPF ROMHE ADTOF OOTTH EROOM HADTH EODDI NTERE STFOR THEES TABLI SHMEN TOFTH EROYA LGEOR GETHA TALTH OUGHB UTONE KINDO FMANW ASSEE NTOGO INTOI TALLK INDSA NDVAR IETIE SOFME NCAME OUTOF ITCON SEQUE NTLYA NOTHE RDRAW ERAND TWOPO RTERS ANDSE VERAL MAIDS ANDTH ELAND LADYW EREAL LLOIT ERING BYACC IDENT ATVAR IOUSP OINTS OFTHE ROADB ETWEE NTHEC ONCOR DANDT HECOF FEERO OMWHE NAGEN TLEMA NOFSI XTYFO RMALL YDRES SEDIN ABROW NSUIT OFCLO THESP RETTY WELLW ORNBU TVERY WELLK EPTWI THLAR GESQU ARECU FFSAN DLARG EFLAP STOTH EPOCK ETSPA SSEDA LONGO NHISW AYTOH ISBRE AKFAS T
```

ciphertext of found3:
```
FIPJS EJXYV CYYHZ KMOYH GNEYN XSYSI PHJOM OKLYY HBTXH MLIYI RGGKK PMFHJ GMJRX GNOVT ZHCSL ZVBAL ZOVKZ RHTWL BLGDJ YGIWO HULMF ZVVKX YDXUU NNRMR AMGZX KSXQR VNBBA IELOP BTZLF MRJET GBUCX RSIYK OPDCY YHRBT UOWAP RPKHM DLCMV VYDMS VCSIU GWHQS MOPRM TUNAY DEYOM AVITL MAUYP DJMCL VYUYY ALDXB IDPXK QQMGZ XKCPC PONTW JVSQP EAJPL BIMQE SOGLD IVEYE KAPCW FZIFG GKLYA VPRYM VYXFZ YTNIS KMLHI EKMYS QFPAB XXHXS BOPVZ MSOWJ PIXIK PCTDW EKKGD SKQPX GOGNF IPJGY ULLDS FTWUK TKGLG NLJOZ PDMQE SOKIY OWSXI QCTZW EBPSS NTPBF SEAUO VOVSM VIQLT YWSPP EFZAV EKFTX JKKLC TSYJE UFMSP YXIAZ LVPWG WOBXZ SKWQS MFRBU ORRSS HMAUY XMQES OGLXI QDMAG VJYVB LRPKP PDLFT WFZHJ UMLRW JGLHC AFTXR GLARI RZTFU YARIU LZRYM OKXZC SXKNW YRRSI AKBNR FMFVV TZIOE ASSEZ ALCTC NOFUY ZKMJE LNZZS SRRPH VTMOO WSYPV MAAPE PLXFK THPEA PLNHB AEEJW CFAIW BIQDI QGGKA YGPXR JPHCW RTPYR BNRXC OYCAG KOVRS IDATP XXUTK OETWK MPZJZ UBZDF PTKUZ XFOWR SEGOM TEWRS EIKVV CXRSI VXHDX IPTRL KTYCK MYIOE LVWIN LMAYM VNVGW PGUMO OGMXT BYXKK RBCIF KKCOH CITEK LZSSL ZJGKE SCSLD FNTDO OLYOE UKTSD LWNSY UNYSR FTWPN XLUWY YHUOL MKGCE LBAZO VMLPH OUKLP IUEVN IXZYJ YYBVK MFLYR AIENT WCXFP GBTYP NILEM NRUHM LCWSE IELBO QTRGK ESCSL DFNTD DOVCA VVTVP ZEJWC BIVBZ MCOAV ZAARI ALVRY HMYXF PVCKH WVIYY HCKKO KTQDI PUGKR ELOGN XXZVM IPWRI HUNLY YHPRH ARIQN SZKXH CMJJS SLTUN SLNSZ VELDM LRLVY KLCIK MPNTV LDSYX EACAV GEQDM GZBUQ JMCLV YIVBX PLMGS KSYVP JHEUI WOHMQ JGULS OINEL RGKYS ZYWSS NBZLV CLOSG LABSS DIQNB TKRBS IFGBK DSRSI QXTDO VYDLR SHCOH FTWPN TPBXM TXVCB ZREAN SZSHK KXGZR CXXWK VCOJB XTFYY LRPNJ RDRSK LCPUF LRIPP EGGGF DMKPX BJTFC LCXEL GLRPS PXVWG KCSWJ ZVEEH YCLCX ELUGS IEQVJ BXTNO RRWIZ GGMBS KEIYR LVXWZ LRXVE LKWCE SYKMT OOLZA LKLZS VRPPY YHUCF YYOVT EVXHM YWVXR LCCCD WVXPL RETPS SZXUD MKPWG NXOYR MFVGU XUDIP EEVTR VEVEP RGRXT ORGYX UKBYD VYGIY RBUQF YNOJG KKCEL OJBXP HBHQM IGCBE DPMYH BTTUN TYCMF YBYKZ YDXQK TSYJR CEIKE SSRED MEOGA OPJDS AGGKM SKAEA ELOYY QPCRY PLKVC BYVZX HPVCY GUNHB CIYDA RREHC ELPRT RBZRS LPCRY LPBRM EQHIA PXXFP LNHBA YJQFG UZKHF IJWMA MRVEV QPPSO MOSRI DMETH AYJJL XREXH BWGEM FLBMD ICYCR GKZCM LNIJK LPXGC TGNSX SKWRQ VBSYY KRAP
```
plaintext of found3:
```
VERYO RDERL YANDM ETHOD ICALH ELOOK EDWIT HAHAN DONEA CHKNE EANDA LOUDW ATCHT ICKIN GASON OROUS SERMO NUNDE RHISF LAPPE DWAIS TCOAT ASTHO UGHIT PITTE DITSG RAVIT YANDL ONGEV ITYAG AINST THELE VITYA NDEVA NESCE NCEOF THEBR ISKFI REHEH ADAGO ODLEG ANDWA SALIT TLEVA INOFI TFORH ISBRO WNSTO CKING SFITT EDSLE EKAND CLOSE ANDWE REOFA FINET EXTUR EHISS HOESA NDBUC KLEST OOTHO UGHPL AINWE RETRI MHEWO REANO DDLIT TLESL EEKCR ISPFL AXENW IGSET TINGV ERYCL OSETO HISHE ADWHI CHWIG ITIST OBEPR ESUME DWASM ADEOF HAIRB UTWHI CHLOO KEDFA RMORE ASTHO UGHIT WERES PUNFR OMFIL AMENT SOFSI LKORG LASSH ISLIN ENTHO UGHNO TOFAF INENE SSINA CCORD ANCEW ITHHI SSTOC KINGS WASAS WHITE ASTHE TOPSO FTHEW AVEST HATBR OKEUP ONTHE NEIGH BOURI NGBEA CHORT HESPE CKSOF SAILT HATGL INTED INTHE SUNLI GHTFA RATSE AAFAC EHABI TUALL YSUPP RESSE DANDQ UIETE DWASS TILLL IGHTE DUPUN DERTH EQUAI NTWIG BYAPA IROFM OISTB RIGHT EYEST HATIT MUSTH AVECO STTHE IROWN ERINY EARSG ONEBY SOMEP AINST ODRIL LTOTH ECOMP OSEDA NDRES ERVED EXPRE SSION OFTEL LSONS BANKH EHADA HEALT HYCOL OURIN HISCH EEKSA NDHIS FACET HOUGH LINED BOREF EWTRA CESOF ANXIE TYBUT PERHA PSTHE CONFI DENTI ALBAC HELOR CLERK SINTE LLSON SBANK WEREP RINCI PALLY OCCUP IEDWI THTHE CARES OFOTH ERPEO PLEAN DPERH APSSE CONDH ANDCA RESLI KESEC ONDHA NDCLO THESC OMEEA SILYO FFAND ONCOM PLETI NGHIS RESEM BLANC ETOAM ANWHO WASSI TTING FORHI SPORT RAITM RLORR YDROP PEDOF FTOSL EEPTH EARRI VALOF HISBR EAKFA STROU SEDHI MANDH ESAID TOTHE DRAWE RASHE MOVED HISCH AIRTO ITIWI SHACC OMMOD ATION PREPA REDFO RAYOU NGLAD YWHOM AYCOM EHERE ATANY TIMET ODAYS HEMAY ASKFO RMRJA RVISL ORRYO RSHEM AYONL YASKF ORAGE NTLEM ANFRO MTELL SONSB ANKPL EASET OLETM EKNOW YESSI RTELL SONSB ANKIN LONDO NSIRY ESYES SIRWE HAVEO FTENT IMEST HEHON OURTO ENTER TAINY OURGE NTLEM ENINT HEIRT RAVEL LINGB ACKWA RDSAN DFORW ARDSB ETWIX TLOND ONAND PARIS SIRAV ASTDE ALOFT RAVEL LINGS IRINT ELLSO NANDC OMPAN YSHOU SEYES WEARE QUITE AFREN CHHOU SEASW ELLAS ANENG LISHO NEYES SIRNO TMUCH INTHE HABIT OFSUC HTRAV ELLIN GYOUR SELFI THINK SIRNO TOFLA TEYEA RSITI SFIFT EENYE ARSSI NCEWE SINCE ICAME LASTF ROMFR ANCE
```

ciphertext of krypton6:
```
BELOS Z
```

plaintext of krypton6:
```
RANDO M
```

key `KEYLENGTH`

password is `RANDOM` for next level

<br><br><br><br><br>






## Krypton 6
### Level Info
Hopefully by now its obvious that encryption using repeating keys is a bad idea. Frequency analysis can destroy repeating/fixed key substitution crypto.

A feature of good crypto is random ciphertext. A good cipher must not reveal any clues about the plaintext. Since natural language plaintext (in this case, English) contains patterns, it is left up to the encryption key or the encryption algorithm to add the ‘randomness’.

Modern ciphers are similar to older plain substitution ciphers, but improve the ‘random’ nature of the key.

An example of an older cipher using a complex, random, large key is a vigniere using a key of the same size of the plaintext. For example, imagine you and your confident have agreed on a key using the book ‘A Tale of Two Cities’ as your key, in 256 byte blocks.

The cipher works as such:

Each plaintext message is broken into 256 byte blocks. For each block of plaintext, a corresponding 256 byte block from the book is used as the key, starting from the first chapter, and progressing. No part of the book is ever re-used as key. The use of a key of the same length as the plaintext, and only using it once is called a “One Time Pad”.

Look in the krypton6 directory. You will find a file called ‘plain1’, a 256 byte block. You will also see a file ‘key1’, the first 256 bytes of ‘A Tale of Two Cities’. The file ‘cipher1’ is the cipher text of plain1. As you can see (and try) it is very difficult to break the cipher without the key knowledge.

If the encryption is truly random letters, and only used once, then it is impossible to break. A truly random “One Time Pad” key cannot be broken. Consider intercepting a ciphertext message of 1000 bytes. One could brute force for the key, but due to the random key nature, you would produce every single valid 1000 letter plaintext as well. Who is to know which is the real plaintext?!?

Choosing keys that are the same size as the plaintext is impractical. Therefore, other methods must be used to obscure ciphertext against frequency analysis in a simple substitution cipher. The impracticality of an ‘infinite’ key means that the randomness, or entropy, of the encryption is introduced via the method.

We have seen the method of ‘substitution’. Even in modern crypto, substitution is a valid technique. Another technique is ‘transposition’, or swapping of bytes.

Modern ciphers break into two types; symmetric and asymmetric.

Symmetric ciphers come in two flavours: block and stream.

Until now, we have been playing with classical ciphers, approximating ‘block’ ciphers. A block cipher is done in fixed size blocks (suprise!). For example, in the previous paragraphs we discussed breaking text and keys into 256 byte blocks, and working on those blocks. Block ciphers use a fixed key to perform substituion and transposition ciphers on each block discretely.

Its time to employ a stream cipher. A stream cipher attempts to create an on-the-fly ‘random’ keystream to encrypt the incoming plaintext one byte at a time. Typically, the ‘random’ key byte is xor’d with the plaintext to produce the ciphertext. If the random keystream can be replicated at the recieving end, then a further xor will produce the plaintext once again.

From this example forward, we will be working with bytes, not ASCII text, so a hex editor/dumper like hexdump is a necessity. Now is the right time to start to learn to use tools like cryptool.

In this example, the keyfile is in your directory, however it is not readable by you. The binary ‘encrypt6’ is also available. It will read the keyfile and encrypt any message you desire, using the key AND a ‘random’ number. You get to perform a ‘known ciphertext’ attack by introducing plaintext of your choice. The challenge here is not simple, but the ‘random’ number generator is weak.

As stated, it is now that we suggest you begin to use public tools, like cryptool, to help in your analysis. You will most likely need a hint to get going. See ‘HINT1’ if you need a kicktstart.

If you have further difficulty, there is a hint in ‘HINT2’.

The password for level 7 (krypton7) is encrypted with ‘encrypt6’.

Good Luck!

### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton6@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
krypton6@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton6@krypton:~$ cd /krypton/
krypton6@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton6@krypton:/krypton$ cd krypton6
krypton6@krypton:/krypton/krypton6$ ls
encrypt6  HINT1  HINT2  keyfile.dat  krypton7  onetime  README
krypton6@krypton:/krypton/krypton6$ cat README 
Hopefully by now its obvious that encryption using repeating keys
is a bad idea.  Frequency analysis can destroy repeating/fixed key
substitution crypto.

A feature of good crypto is random ciphertext.  A good cipher must
not reveal any clues about the plaintext.  Since natural language 
plaintext (in this case, English) contains patterns, it is left up
to the encryption key or the encryption algorithm to add the 
'randomness'.

Modern ciphers are similar to older plain substitution 
ciphers, but improve the 'random' nature of the key.

An example of an older cipher using a complex, random, large key
is a vigniere using a key of the same size of the plaintext.  For
example, imagine you and your confident have agreed on a key using
the book 'A Tale of Two Cities' as your key, in 256 byte blocks.

The cipher works as such:

Each plaintext message is broken into 256 byte blocks.  For each 
block of plaintext, a corresponding 256 byte block from the book
is used as the key, starting from the first chapter, and progressing.
No part of the book is ever re-used as key.  The use of a key of the 
same length as the plaintext, and only using it once is called a "One Time Pad".

Look in the krypton6/onetime  directory.  You will find a file called 'plain1', a 256 
byte block.  You will also see a file 'key1', the first 256 bytes of
'A Tale of Two Cities'.  The file 'cipher1' is the cipher text of 
plain1.  As you can see (and try) it is very difficult to break
the cipher without the key knowledge.

(NOTE - it is possible though.  Using plain language as a one time pad
key has a weakness.  As a secondary challenge, open README in that directory)

If the encryption is truly random letters, and only used once, then it
is impossible to break.  A truly random "One Time Pad" key cannot be
broken.  Consider intercepting a ciphertext message of 1000 bytes.  One
could brute force for the key, but due to the random key nature, you would
produce every single valid 1000 letter plaintext as well.  Who is to know
which is the real plaintext?!?

Choosing keys that are the same size as the plaintext is impractical.
Therefore, other methods must be used to obscure ciphertext against 
frequency analysis in a simple substitution cipher.  The
impracticality of an 'infinite' key means that the randomness, or
entropy, of the encryption is introduced via the method.

We have seen the method of 'substitution'.  Even in modern crypto,
substitution is a valid technique.  Another technique is 'transposition',
or swapping of bytes.

Modern ciphers break into two types; symmetric and asymmetric.

Symmetric ciphers come in two flavours: block and stream.

Until now, we have been playing with classical ciphers, approximating
'block' ciphers.  A block cipher is done in fixed size blocks (suprise!).
For example, in the previous paragraphs we discussed breaking text and keys
into 256 byte blocks, and working on those blocks.  Block ciphers use a
fixed key to perform substituion and transposition ciphers on each
block discretely.

Its time to employ a stream cipher.  A stream cipher attempts to create
an on-the-fly 'random' keystream to encrypt the incoming plaintext one
byte at a time.  Typically, the 'random' key byte is xor'd with the 
plaintext to produce the ciphertext.  If the random keystream can be
replicated at the recieving end, then a further xor will produce the
plaintext once again.

From this example forward, we will be working with bytes, not ASCII 
text, so a hex editor/dumper like hexdump is a necessity.  Now is the
right time to start to learn to use tools like cryptool.

In this example, the keyfile is in your directory, however it is 
not readable by you.  The binary 'encrypt6' is also available.
It will read the keyfile and encrypt any message you desire, using
the key AND a 'random' number.  You get to perform a 'known ciphertext'
attack by introducing plaintext of your choice.  The challenge here is 
not simple, but the 'random' number generator is weak.

As stated, it is now that we suggest you begin to use public tools, like cryptool,
to help in your analysis.  You will most likely need a hint to get going.
See 'HINT1' if you need a kicktstart.

If you have further difficulty, there is a hint in 'HINT2'.

The password for level 7 (krypton7) is encrypted with 'encrypt6'.

Good Luck!
krypton6@krypton:/krypton/krypton6$ cat HINT1
The 'random' generator has a limited number of bits, and is periodic.
Entropy analysis and a good look at the bytes in a hex editor will help.

There is a pattern!
krypton6@krypton:/krypton/krypton6$ cat HINT2
8 bit LFSR
krypton6@krypton:/krypton/krypton6$ 





krypton6@krypton:/krypton/krypton6$ ls
encrypt6  HINT1  HINT2  keyfile.dat  krypton7  onetime  README
krypton6@krypton:/krypton/krypton6$ cat keyfile.dat
cat: keyfile.dat: Permission denied
krypton6@krypton:/krypton/krypton6$ cat onetime
cat: onetime: Is a directory
krypton6@krypton:/krypton/krypton6$ cd onetime/
krypton6@krypton:/krypton/krypton6/onetime$ ls
cipher1  key1  plain1
krypton6@krypton:/krypton/krypton6/onetime$ cat cipher1 
ABJGGZVHEIKLHMXIZKWZHBAUAPPHSJKHBTYXQPWCLPHSMIVOAKVYYWMQHXMLOIDEZYPURHMJOQSIWHAWESVRWBJTCIWDINKWIJXDMRIPNNRQBUKHDKPACMIQGJEQXXIGWIAARGWPHAXYASYRFAZKFMWWKGKTUHNYLLIESXIOICBAWJMMDEUHBRKTCABLXTCSUYTYELDXKJNWZMLVRFBSFLHQTDXOEVSISWYMYMHYLMSUFJGWJEUDJESTAIPNJPQkrypton6@krypton:/krypton/krypton6/onetime$ 
krypton6@krypton:/krypton/krypton6/onetime$ cat key1 
ITWASTHEBESTOFTIMESITWASTHEWORSTOFTIMESITWASTHEAGEOFWISDOMITWASTHEAGEOFFOOLISHNESSITWASTHEEPOCHOFBELIEFITWASTHEEPOCHOFINCREDULITYITWASTHESEASONOFLIGHTITWASTHESEASONOFDARKNESSITWASTHESPRINGOFHOPEITWASTHEWINTEROFDESPAIRWEHADEVERYTHINGBEFOREUSWEHADNOTHINGBEF
krypton6@krypton:/krypton/krypton6/onetime$ cat plain1 
SINGOGODDESSTHEANGEROFACHILLESSONOFPELEUSTHATBROUGHTCOUNTLESSILLSUPONTHEACHAEANSMANYABRAVESOULDIDITSENDHURRYINGDOWNTOHADESANDMANYAHERODIDITYIELDAPREYTODOGSANDVULTURESFORSOWERETHECOUNSELSOFJOVEFULFILLEDFROMTHEDAYONWHICHTHESONOFATREUSKINGOFMENANDGREATACHILL
krypton6@krypton:/krypton/krypton6/onetime$ cd ..
krypton6@krypton:/krypton/krypton6$ cat krypton7 
PNUKLYLWRQKGKBE


krypton6@krypton:/krypton/krypton6$ ./encrypt6
usage: encrypt6 foo bar 
Where: foo is the file containing the plaintext and bar is the destination ciphertext file.


krypton6@krypton:/krypton/krypton6$ ls
encrypt6  HINT1  HINT2  keyfile.dat  krypton7  onetime  README
krypton6@krypton:/krypton/krypton6$ mktemp -d
/tmp/tmp.oaS8SUFWf9
krypton6@krypton:/krypton/krypton6$ cd /tmp/tmp.oaS8SUFWf9
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ ln -s /krypton/krypton6/keyfile.dat 
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ ls
keyfile.dat
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ vi plain
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ cat plain 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ ls
keyfile.dat  plain
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ /krypton/krypton6/encrypt6 
usage: encrypt6 foo bar 
Where: foo is the file containing the plaintext and bar is the destination ciphertext file.
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ /krypton/krypton6/encrypt6 plain cipher
failed to open keyfile 
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ chmod 777 /tmp/tmp.oaS8SUFWf9
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ /krypton/krypton6/encrypt6 plain cipher
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ ls
cipher  keyfile.dat  plain
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ cat cipher 
EICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGkrypton6@krypton:/tmp/tmp.oaS8SUFWf9$ 
krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ 



krypton6@krypton:/tmp/tmp.oaS8SUFWf9$ exit
logout
Connection to krypton.labs.overthewire.org closed.


```

cipher
```
EICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGkrypton6
```

based on observation, the `EICTDGYIYZKTHNSIRFXYCPFUEOCKRN`is the repeating things, thus, it is the key

after decypting the ciphertext `PNUKLYLWRQKGKBE` using the key above, the plaintext obtained `LFSRISNOTRANDOM`

<br><br><br><br><br>






## Krypton 7
### Execution Log
```
┌──(incognito㉿kali)-[~]
└─$ ssh krypton7@krypton.labs.overthewire.org -p 2231
                      _                     _              
                     | | ___ __ _   _ _ __ | |_ ___  _ __  
                     | |/ / '__| | | | '_ \| __/ _ \| '_ \ 
                     |   <| |  | |_| | |_) | || (_) | | | |
                     |_|\_\_|   \__, | .__/ \__\___/|_| |_|
                                |___/|_|                   

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
krypton7@krypton.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

krypton7@krypton:~$ cd /krypton/
krypton7@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6  krypton7
krypton7@krypton:/krypton$ cd krypton7
krypton7@krypton:/krypton/krypton7$ ls
README
krypton7@krypton:/krypton/krypton7$ cat README 
Congratulations on beating Krypton!
krypton7@krypton:/krypton/krypton7$ exit
logout
Connection to krypton.labs.overthewire.org closed.
```
