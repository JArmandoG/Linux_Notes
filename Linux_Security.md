# General Linux Security Modules + Cryptography

## MAC Address

MAC Address manual/Crontab change:

```
sudo apt install macchanger -y
```

(* Virtual Machines don't inherit the Host's MAC address)

## SERIAL NUMBERS

```
dmidecode -t <option>

# Or:

lshw --class 'disk' (Or other options)
```

- VM have a different SN than Hosts

# ACM
(Access control model)
- Discretionary Access Control (DAC)
Sudo, Wheel/sudoers - User/administrator's decision. Subject - Object model

- NDAC - Non-discretionary Access Control
- RBAC - Role-Based Access Control (Grupos)

- MAC - Mandatory Access Control 
Groups & Subjects/Accesses. Privileged access model object by clearance. Example: `SELinux`

# SECURITY FRAMEWORKS

[Firejail, SELinux, AppArmor](https://www.youtube.com/watch?v=JFjXvIwAeVI&t=23s)


Frameworks, Software, Modules

- GrSecurity / AppArmor / SELinux

	Apparmor -> Per program & permissions.
Easiest to setup. Lightweight. 

	SELinux -> Implements MAC model
Limits permissions of programs/users. Static servers. HEAVY ADMINISTRATION.

	GrSecurity -> Low configuration. Not default. 
Link: https://micahflee.com/2016/01/debian-grsecurity/ (Comprensivo)
Link: https://grsecurity.net/compare

Comparison: (OLD) https://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html

	PAX -> Patch 4 linux kernel. Least-privilege approach. PaX + Frameworks
Link: https://alpinelinux.org/downloads/

LSM (Linux Security Modules)
https://en.wikipedia.org/wiki/Linux_Security_Modules

Pentoo, Alpine (Security/lightweight), Arch Linu (Uses PaX & GrSecurity)

GrSecurity enabled kernels for debian: ColdKernel

# Cryptography
	
## OpenSSL:
	
> In - `$ openssl camellia-256-cbc -salt -in my_file.txt -out encrypted.txt -pbkdf2`
> Out - `$ openssl camellia-256-cbc -d -in encrypted.txt -out decrypted.txt -pbkdf2`
	
## PBKDF: 
\** Password-Based Key Derivation Function*
[KDF](https://en.wikipedia.org/wiki/Key_derivation_function) != [PBKDF](https://en.wikipedia.org/wiki/PBKDF2)
	
> PBKDF -> Slows down hashing process to thwart Brute-force attacks
	
## Asymmetric Key Cryptography
	
> KeyGen - (public key , private key)
> Encrypt(text, public key) -> Ciphertext
> Decrypt (ciphertext , private key ) -> Text

> Sign (data , private key ) -> Signature
> Verify (data, signature , public key ) -> True / False
(RSA general implementation)

#### PGP

Pgp Inc. Established OpenPGP as a standard. GnuPG is a [Free Software Foundation](https://www.fsf.org/) software that implements OpenPGP.

-   [PGP (Pretty Good Privacy) email encryption](https://en.wikipedia.org/wiki/Pretty_Good_Privacy). Host PHP keys online e.g. in a PGP keyserver, or on [Keybase](https://keybase.io/) -> Sign and send/receive encrypted email.
-   Private messaging. Apps like [Signal](https://signal.org/) and [Keybase](https://keybase.io/) use asymmetric keys to establish private communication channels.
-   Signing software. Git can have GPG-signed commits and tags. With a posted public key, anyone can verify the authenticity of downloaded software.

> **Infrastructure:** 
> The first version of this system was generally known as a [web of trust](https://en.wikipedia.org/wiki/Web_of_trust "Web of trust") to contrast with the [X.509](https://en.wikipedia.org/wiki/X.509 "X.509") system, which uses a hierarchical approach based on [certificate authority](https://en.wikipedia.org/wiki/Certificate_authority "Certificate authority") and which was added to PGP implementations later. -- \*[Wikipedia](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)

**PGP** - Pretty Good Privacy: **Software**. Implements Public Key Cryptography
**OpenPGP** - Standard, RFC 4880: Implements PGP
**GnuPG** - Gnu Privacy Guard: Software, FOSS. Implements OpenPGP

> --Sender--
> - Encrypt( Data , Random_key_gen ) -> ciphertext
> - Encrypt( Random_key , Dest.Public_key) -> Encrypted.Key
>
> --Receiver--
> - Decrypt(Encrypted.Key , Dest.Private_key) -> Key
> - Decrypt(Ciphertext , Key) -> Data
>



