# Use Faster Public DNS Servers
## Replace your current nameservers with fast and reliable ones like Google DNS, Cloudflare, or OpenDNS.

    sudo nano /etc/resolv.conf

### And replace its content with:

### Google DNS

    nameserver 8.8.8.8
    nameserver 8.8.4.4

### Cloudflare DNS

    nameserver 1.1.1.1
    nameserver 1.0.0.1

OpenDNS

    nameserver 208.67.222.222
    nameserver 208.67.220.220

## Reduce Timeout and Optimize Options
## Add these lines to improve DNS performance:

    options timeout:1
    options attempts:2
    options rotate
    options single-request-reopen

timeout:1 → Reduces DNS query timeout to 1 second (default is 5s).
attempts:2 → Limits retry attempts to 2 (default is 5).
rotate → Uses multiple DNS servers in a round-robin fashion.
single-request-reopen → Prevents delays due to IPv6/IPv4 mismatches.

## Make resolv.conf Immutable (Optional)
## Many systems overwrite /etc/resolv.conf. To prevent this:

    sudo chattr +i /etc/resolv.conf

## To allow modifications again:

    sudo chattr -i /etc/resolv.conf


##  Use a Local DNS Cache (Recommended)
## For better performance, install a local caching DNS resolver like dnsmasq or unbound:

    sudo apt install dnsmasq

## Then, set /etc/resolv.conf to:

    nameserver 127.0.0.1

## This caches DNS queries locally, reducing lookup time.

##  Flush DNS Cache
## If using a local cache or systemd-resolved, clear the cache:

    sudo systemctl restart systemd-resolved
    sudo systemd-resolve --flush-caches











