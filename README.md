# hakip2host
hakip2host takes a list of IP addresses via stdin, then does a series of checks to return associated domain names.

Current supported checks are:

- DNS PTR lookups
- Subject Alternative Names (SANs) on SSL certificates
- Common Names (CNs) on SSL certificates

## Usage

Download the relevant binary from the releases page: 
https://github.com/NHAS/hakip2host/releases

Or install golang and install manually:

```
go install github.com/NHAS/hakip2host@latest
```

## Help

```sh
./hakip2host --help
  -f string
        Output format, supports text, json (default "text")
  -p int
        Port to bother the specified DNS resolver on (default 53)
  -protocol string
        Protocol for DNS lookups (tcp or udp) (default "udp")
  -r string
        IP of DNS resolver for lookups
  -t int
        numbers of threads (default 32)
```

## Example usage

```sh
hakluke$ prips 173.0.84.0/24 | ./hakip2host
[DNS-PTR] 173.0.84.23 new-creditcenter.paypal.com
[DNS-PTR] 173.0.84.11 slc-a-origin-www-1.paypal.com
[DNS-PTR] 173.0.84.10 admin.paypal.com
[DNS-PTR] 173.0.84.30 ss-www.paypal.com
[DNS-PTR] 173.0.84.5 www.gejscript-paypal.com
[DNS-PTR] 173.0.84.24 slc-a-origin-demo.paypal.com
[DNS-PTR] 173.0.84.20 origin-merchantweb.paypal.com
[SSL-SAN] 173.0.84.67 uptycspay.paypal.com
[SSL-SAN] 173.0.84.67 a.paypal.com
[SSL-CN] 173.0.84.67 api.paypal.com
[SSL-SAN] 173.0.84.76 svcs.paypal.com
[SSL-SAN] 173.0.84.76 uptycshon.paypal.com
[SSL-SAN] 173.0.84.76 uptycshap.paypal.com
[SSL-SAN] 173.0.84.76 uptycsven.paypal.com
[SSL-SAN] 173.0.84.76 uptycsize.paypal.com
[SSL-SAN] 173.0.84.76 uptycspay.paypal.com
[SSL-CN] 173.0.84.76 svcs.paypal.com
```
