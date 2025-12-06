# Chapter 41. Getting started with nftables

1. The **nftables** is the successor to the **iptables**, **ip6tables**, **arptables**, **ebtables**, and **ipset** utilities.
It delivers many gains in convenience, functionality, and performance compared with earlier packet-filtering tools, especially:
    - Built-in lookup tables instead of linear processing
    - A single framework for both the **IPv4** and **IPv6** protocols
    - Updating the kernel rule set in place through transactions instead of fetching, updating, and storing the entire rule set
    - Support for debugging and tracing in the rule set (**nftrace**) and monitoring trace events (in the **nft** tool)
    - More consistent and compact syntax, no protocol-specific extensions
    - A Netlink API for third-party applications

