A Domain Name System translates a domain name (like <www.srf.ch>) to an IP Address.
![[DNS Hirarchy.png]]

## DNS Servers
### Root DNS Server
Is called by IP Anycast to automatically reach the closest root DNS Server. These servers are hosted by 13 organizations around the world.

### Authoritative nameserver
A server which contains a [[#DNS Zone]].

## DNS resolving
There are two ways of resolving an address per DNS:
- **Iterative DNS**: If the DNS Server does not know the requested address, it returns the address of the next (lower) DNS Server who might know the name. It is up to the client to contact this new Server.
- **Recursive DNS**: If the DNS Server does not know the requested address, it will make additional requests to other DNS Servers to satisfy the clients need and returns the address. The client does not need to make further requests.

### Load Balancing
Usually, DNS Servers return multiple IP Addresses associated with a domain. The clients DNS Resolver will choose one of them. This balances load and enhances fault tolerance.

### Caching
A DNS Resolver will store acquired DNS Records to reduce DNS traffic on name servers. This applies for client and DNS Server. Each record contains a Time to Live (**TTL**) variable which dictates how long a Record will be kept before discarding.

#### DNS cache Poisoning
Also known as _DNS Spoofing_. The act of entering false Records into the DNS Cache in order to forward Users onto wrong websites.

##### DNSSEC
Short for _Domain Name System Security Extensions_. Uses public key cryptography to authenticate DNS Data to avoid cache poisoning.

## DNS Zone
Each authoritative Nameserver contains a Zone, which is a collection of key value entries (e.g. <www.ost.ch>: 146.136.105.95).

### Record Types

| Type | Full Name | Meaning | Example |
| ---- | ---- | ---- | ---- |
| A |  | IPv4 Address | `vpn.ost.ch, 152.96.1.36, A,<TTL default:14400s`<br> |
| AAAA |  | IPv6 Address | `www.ost.ch, 2001:620:1c0:b105:0:1ff:fe05:9, AAAA, <TTL default:14400s>` |
| CNAME | Canonical Name | Points to another domain name | `ost.ch, <www.ost.ch>, CNAME, <TTL>` |
| MX | Mail Exchange | Maps to domain of mail server | `ost.ch, mail.ost.ch, MX, <TTL>` |
| NS | Name Server | Points to the authoritative name server of this domain | `ost.ch, dns01.ost.ch, NS, <TTL>` |
| PTR | Pointer | Returns domain name for an IP address | `36.1.96.152.in-addr.arpa, vpn.ost.ch, PTR` |
| SOA | Start of Authority | States information about domain. | For example server admin email, last domain update, how long the server waits between refreshes |
| SRV | Service | Specifies ports for specific services | For example for VOIP |
| TXT | Text | Stores additional data. | Used for Sender Policy Framework (SPF) & Domain Keys Identified Mail (DKIM) |
