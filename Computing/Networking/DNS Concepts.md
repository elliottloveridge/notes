# DNS Concepts
> [The Only 6 DNS Concepts You Really Need](https://jonahdevs.com/youre-closer-than-you-think-the-only-6-dns-concepts-you-really-need/?utm_source=tldrnewsletter)

- **A Records**: Your domain's home address
	- If you create an endpoint (IP) address of 203.0.113.10. then you would create an A record that points to this
		- yourwebsite.com. IN A 203.0.11.1
		- When someone types in yourwebsite.com the A record tells them to go to this specific IP address to find your websites content
- **CNAME**: Your domain's nickname generator
	- Your want both `yourwebsite.com` and `www.yourwebsite.com` to lead to the same place
	- You'd setup a CNAME record like: `www.yourwebsite.com`. IN CNAME coolsite.com
		- You're saying it's just another name for coolsite.com
		- The target **must** be a domain name, never an IP address
- **MX Records**: Directing your digital mail
	- MX records are all about email
	- They tell the world which servers handle the email for your domain
		- If you're using Google Workspace for email, you'd setup an MX record like this:
			- yourwebsite.com. IN MX 1 ASPMX.L.GOOGLE.COM.
				- 1 is the priority (you can have multiple MX records to try)
- **TXT Records**: 'Wild cards' of DNS
	- A place to stash any text-based information about your domain
- **NS Records**: Crucial for the hierarchical structure of DNS
	- NS (Name Server) records tell the internet which servers are authoritative for your domain's DNS information
- **TTL Records**: The expiry date of your DNS cache
	- Time To Live (TTL) is how long DNS information is cached