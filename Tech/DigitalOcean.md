# Web Hosting Provider
I hold an account here where I host several web applications/websites.
I also manage the DNS of several of the [[Domains]] I own here.

## Droplets
Virtual machines on this provider are referred to as 'droplets'.
Each droplet is technically a shared virtual machine with shared RAM, CPU, HDD etc.

As of [[2024-05-30]], I have 3 running droplets.  I've created a new one [[2024-05-29]] to host applications specifically for [[Total Tent Rental]] company that I plan on starting (am currently working on starting).

As of [[2024-07-01]], I destroyed the SuperFastHomes droplet.  It was running me $21/month and it had been 'turned off' for several months.  I officially killed it today.  Hopefully there wasn't anything important on that box :(




## DNS
In order to manage the DNS for a domain that you've purchased elsewhere, you need to go to the Domain's Registrar website, navigate to the 'Manage DNS' area and tell them that you want to use custom DNS Nameservers.

Then, where required, enter the 3 DigitalOcean Name Server addresses:
- ns1.digitalocean.com
- ns2.digitalocean.com
- ns3.digitalocean.com