hashcat

Basic NTLMv1 Hashcat Example

~~~cmd
hashcat.exe -D 2 -m 1000 hashes.txt dictionary_file.txt -O -o decrypted_hashes.txt
~~~

Switches used in example:
   ◇ -D → Specifies device to use for cracking (1 == CPU | 2 == GPU | 3 == Co-Processor)
   ◇ -m → Specifies mode/type of hash being cracked (see hash types examples above)
   ◇ -O → Optimized setting
   ◇ -o → output file created with decrypted hashes

Example of NTLMv2 hash with wordlist and rules

~~~cmd
hashcat.exe -m 5600 ..\hash.txt ..\Wordlists\rockyou2021.txt -O -o ..\decrypted_hash.txt -r rules\cyclone_250.rule --debug-mode=1 --debug-file=matched.rules -w3
~~~

Example of WPA2 hash with non-dictionary brute-force attack

~~~cmd
hashcat.exe -m 22000 ..\wifihash.txt -a 3 -1 ?l?u?d ?1?1?1?1?1?1?1?1 -O -o ..\wifihash_decrypted.txt
~~~