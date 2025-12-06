# Chapter 41. Getting started with nftables

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

* 41.1. Creating and managing nftables tables, chains, and rules