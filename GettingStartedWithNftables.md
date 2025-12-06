# Getting started with nftables

1. **nftables**  is the successor to the **iptables**, **ip6tables**, **arptables**, **ebtables**, and **ipset** utilities.
It delivers many gains in convenience, functionality, and performance compared with earlier packet-filtering tools, especially:
    - Built-in lookup tables instead of linear processing
    - A single framework for both the **IPv4** and **IPv6** protocols
    - Updating the kernel rule set in place through transactions instead of fetching, updating, and storing the entire rule set
    - Support for debugging and tracing in the rule set (**nftrace**) and monitoring trace events (in the **nft** tool)
    - More consistent and compact syntax, no protocol-specific extensions
    - A Netlink API for third-party applications

The **nftables** framework uses tables to store chains. The chains contain individual rules, for performing actions.
The **nft** utility replaces all tools from the previous packet-filtering frameworks. You can use the **libnftables** library for low-level interaction with **nftables** Netlink API through the **libnftnl** library. 

To display the effect of rule set changes, use the **nft list ruleset** command. To clear the kernel rule set, use the **nft flush ruleset** command. Note that this may also affect the rule set installed by the **iptables-nft** command, as it utilizes the same kernel infrastructure. 

## Analysing the difference between nftables and the previous tools

Multiple Tools, Multiple Problems

```
# Before nftables - 4 different tools, 4 different syntaxes
iptables -A INPUT -p tcp --dport 22 -j ACCEPT    # IPv4
ip6tables -A INPUT -p tcp --dport 22 -j ACCEPT   # IPv6  
arptables -A INPUT --source-ip 1.2.3.4 -j ACCEPT # ARP
ebtables -A INPUT -s 00:11:22:33:44:55 -j ACCEPT # Ethernet
```

One Tool, Many Powers

```
# With nftables - one tool for everything
nft add rule ip filter input tcp dport 22 accept
nft add rule ip6 filter input tcp dport 22 accept
nft add rule arp filter input ip saddr 1.2.3.4 accept
nft add rule bridge filter input ether saddr 00:11:22:33:44:55 accept
```