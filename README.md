# dedicated server rentals: what $79 and $235 a month actually buy, is prepaying worth the lock-in, and who should skip the cheap entry plan (full plan table plus market price comparison)

A dedicated server rental costs anywhere from roughly $25 to $1,300 a month, and every advertised price sits at the bottom of that spread: smallest configuration, longest commitment, or both. SpinServers lists a 4-core Xeon E3-1280 v5 with 32GB RAM and a 1TB NVMe drive at $79/month in Dallas, and a dual E5-2630L v3 with 128GB from $235/month. The same pattern runs across the market, with Dedicated.com from $35.75/mo, HOSTKEY from €25/mo, Cherry Servers at about $0.091/hour, and Scaleway's €4.74/mo tied to a 12-month commitment.

What follows is the SpinServers inventory currently on display, the workload each bracket actually handles, the arithmetic behind prepay discounts, what the monthly quote does and does not include, and the situations where renting a box like this is the wrong purchase.

> **Quick pick.** One server for a site, app, API or game instance: the Xeon E3-1280 v5 at $79/month gives you 4 cores, 32GB RAM, 1TB NVMe and 30TB of transfer on a 10Gbps port, which is more headroom than most single-workload deployments use. Move up to the 128GB dual E5-2630L v3 (from $235/month) when you're running several VMs, a database with a large working set, or anything that gets killed by memory pressure. 👉 [check the current Dallas configurations and prices](https://bit.ly/Spinservers)

## The full SpinServers lineup, and which config fits which job

SpinServers sells bare metal in two locations, Dallas and San Jose. Every listing below includes IPMI/iKVM remote management, at least one IPv4 address (plus an IPv6 /64 allocation), and sits on a DDoS-protected, multihomed network. Linux, Windows and ESXi installs are automated, and in-stock machines provision without a human touching them.

| Configuration | Location | Price (monthly) | Network & transfer | Provisioning | Order |
| --- | --- | --- | --- | --- | --- |
| Intel Xeon E3-1280 v5, 4c/8t @3.7GHz, 32GB DDR4 ECC, 1TB NVMe | Dallas | $79 | 10Gbps port, 30TB, 1 IPv4 | Auto-provisions | [check this server](https://bit.ly/Spinservers) |
| Dual Intel Xeon E5-2630L v3, 16c/32t @2.90GHz, 128GB DDR4 ECC, 1TB NVMe | Dallas | from $235 | 10Gbps port, 30TB | Ready to go | [check this server](https://bit.ly/Spinservers) |
| Dual Intel Xeon Gold 6148, 256GB DDR4, 2 x 1.92TB SSD | Dallas | quoted at order | 10Gbps, 30TB | Instant, preconfigured | [check this server](https://bit.ly/Spinservers) |
| Dual Intel Xeon Platinum 8173M, 56c/112t @3.50GHz, 512GB DDR4, 4 x 1.92TB SSD | Dallas | quoted at order | 2 x 10Gbps (LACP), 30TB | Instant, preconfigured | [check this server](https://bit.ly/Spinservers) |
| 12c/24t @2.6GHz, 64GB DDR3 ECC, 240GB SSD | San Jose | quoted at order | 2 x 10Gbps, 30TB, 1 IPv4 | Instant | [check this server](https://bit.ly/Spinservers) |
| 16c/32t @1.8GHz, 64GB DDR4 ECC, 1.6TB NVMe | San Jose | quoted at order | 2 x 10Gbps, 30TB | Instant | [check this server](https://bit.ly/Spinservers) |
| 24c/48t @1.8GHz, 64GB DDR4 ECC, 1.6TB SSD | San Jose | quoted at order | 2 x 10Gbps, 30TB | Instant | [check this server](https://bit.ly/Spinservers) |
| 16c/32t @1.8GHz, 256GB DDR4 ECC, 2 x 1.6TB SSD, hardware RAID | San Jose | quoted at order | 2 x 10Gbps, 30TB | Instant | [check this server](https://bit.ly/Spinservers) |
| 32c/64t @2.1GHz, 512GB DDR4 ECC, 2 x 3.84TB SSD, RAID with battery-backed cache | San Jose | quoted at order | 2 x 10Gbps, 30TB, 1 IPv4 | Instant | [check this server](https://bit.ly/Spinservers) |

Only two price points are posted publicly on the Dallas listing; the rest are quoted on the order page because they track hardware and availability. Inventory rotates, so a configuration that is absent today can reappear next week, and prices move with it.

Reading the table by workload is more useful than reading it by price. The $79 E3-1280 v5 handles a production website, a container host for a handful of services, or a game server with a modest player count. The dual E5-2630L v3 at 128GB is the virtualization bracket: several KVM guests, a MongoDB or PostgreSQL instance that wants to cache aggressively, CI runners, or a render queue. The Gold 6148 and Platinum 8173M configurations exist for people who need storage density and thread count in the same chassis, and the five San Jose machines lean toward dual 10Gbps throughput and hardware RAID, which is a datacenter-to-datacenter replication or storage-server profile rather than a web-hosting one.

## The entry price is the floor of a ladder, not the price you'll pay

The gap between an advertised entry price and a configuration you can actually run production on is the single most reliable way to misjudge a dedicated server rental budget. The public numbers make the ladder visible:

- Dedicated.com advertises $35.75/mo, and its own product page also lists a 36-core/72-thread Xeon Gold 6140 with 256GB RAM, 2 x 2TB SSD and 100TB of transfer at $183.99/mo. That is a five-fold difference inside one provider's catalogue.
- HOSTKEY publishes three official starting points: €99/mo for a Xeon E3 with 16GB and 2 x 1TB HDD, €199/mo for a Xeon Silver with 32GB and 2 x 480GB SSD, €349/mo for an EPYC with 64GB and NVMe. Its own FAQ gives €25/mo as the floor, €100/mo as the average, and €600+/mo for the high end.
- Scaleway's range runs from €4.74/mo for Start (with a 12-month commitment) to €29.74 for Pro and €110.49 for Core on 36-month terms, up to €1,274.99/mo for a GPU machine.
- Cherry Servers quotes from about $0.091/hour, and scales to configurations with up to 128 cores and 2,304GB of RAM.

Two things follow. A cheap headline usually describes a machine with a few cores, 8GB to 32GB of RAM and spinning or small SSD storage, which is fine for a static site and not fine for anything memory-bound. And the price you should budget is the one attached to the configuration that matches your workload, not the one attached to the provider's cheapest SKU.

## Hourly, monthly or prepaid: what the discount actually costs you

Prepay discounts are real, and they are priced as lock-in. Dedicated.com discounts 3% on a 3-month prepay, 6% on 6 months and 12% on 12 months across most configurations. HOSTKEY offers up to 25% off for terms of 6 months or longer and lets annual prepayment fix the price. Cherry Servers advertises up to 50% savings on fixed-term billing against its hourly on-demand rate. Scaleway's lowest monthly figures only exist with 12- or 36-month commitments, and the 36-month figure appears on four of its five product lines.

Converting the discount into money makes the trade-off concrete. Dedicated.com's Gold 6140 configuration at $183.99/mo would cost $2,207.88 over 12 monthly payments; the 12-month prepay is $1,942.93, a saving of $264.95. Its 6-month prepay is $1,037.70 against $1,103.94 monthly, a saving of $66.24. In both cases you hand over the entire sum before you have used a single hour, so the discount is compensation for the risk you are taking on the provider.

SpinServers quotes these configurations monthly, and no prepay schedule is published alongside them. If you expect to stay a year, ask what a longer term does to the price before you order; the market range for that discount is 12% to 25% on 12-month terms, occasionally more.

## What the monthly quote includes, and the one line most buyers miss

Included in every SpinServers configuration above: IPMI/iKVM access, one IPv4 address, an IPv6 /64 block, 30TB of monthly transfer on 10Gbps ports, and DDoS filtering on a multihomed network. That IPv4 count is worth pausing on. One address covers a single public-facing service with no spare for a mail server, a separate staging environment or a second SSL endpoint. Providers differ here: Dedicated.com hands out a /29 on every server, which is 5 usable addresses, while HOSTKEY includes free IPv4 and IPv6. If you need additional addresses, ask what they cost before the order rather than after.

DDoS protection is now table stakes and mostly free at the basic tier. Dedicated.com includes filtering free on every port, HOSTKEY gives basic protection free in Europe with coverage against SYN, ACK, RST, FIN and PUSH floods, and Cherry Servers standardises it across all plans. What differs is the size of attack the basic tier absorbs, which is worth asking about if you have been targeted before.

The line most buyers miss is management. These are unmanaged servers, and that is the industry default rather than a SpinServers quirk. HOSTKEY states plainly that all its servers are unmanaged and that administration is a paid extra. You get root access and IPMI, which means the operating system, patching, firewall rules, backups and application stack are yours. A provider's 24/7 chat support covers the hardware and the network, not your nginx configuration. Budget for either your own time or a management contract, and price the management contract before you compare providers on headline cost. 👉 [see what the SpinServers configurations include](https://bit.ly/Spinservers)

## How fast you get the box

SpinServers operates the fastest model of the four: listed inventory carries an auto-provision flag or an instant preconfigured flag, meaning the machine is racked, imaged and waiting, so it comes up without a technician in the loop. Operating system choice at order covers Linux, Windows and ESXi.

The rest of the market sits in the same range. Dedicated.com deploys in-stock servers the moment payment lands, with the OS install taking about 20 minutes and credentials arriving by email. HOSTKEY says turnkey servers go online a few minutes after payment. Cherry Servers averages 12 minutes for preconfigured hardware, about 24 hours for custom builds, and around 30 minutes for a Windows install.

The practical difference shows up when you need something that is not in stock. A custom configuration, extra RAM, or a specific RAID card pushes you from minutes into hours or days, and every provider on this list has an out-of-stock state on at least part of its catalogue.

## Dallas and San Jose: who those two locations serve, and who they don't

Two locations is a real constraint, and it is the clearest reason to look elsewhere. Dallas covers North America centrally and reaches both US coasts and Latin America with reasonable latency. San Jose covers the US West Coast and, for many networks, trans-Pacific routes to Asia. If your users are in Europe, you are serving them across the Atlantic from either site, and no configuration change fixes that.

European readers should treat this as a hard requirement rather than an optimisation. HOSTKEY runs in Europe, the US and Turkey and notes that European capacity, especially in Germany and the Netherlands, costs 10% to 15% more than US capacity because of energy prices, environmental rules and taxes, with GDPR compliance and local latency as the return on that premium. Cherry Servers offers Lithuania, the Netherlands, Germany, Sweden, the US and Singapore. Scaleway's Dedibox runs on two physically separate networks, and its private RPN network carries inter-server traffic without consuming public bandwidth, which matters if you are building a cluster rather than renting one machine.

If your workload touches EU personal data, hosting in Texas or California means handling transfer mechanisms yourself. Renting a cheaper US box and sorting the paperwork later is a common and expensive mistake.

## When a dedicated server rental is the wrong purchase

Three cases where the answer is to spend less or differently.

**You need someone to run the server.** No unmanaged provider will patch your kernel. If nobody on your side wants that job, add a management contract to the budget or choose a managed offering, and expect the monthly figure to move up rather than sideways.

**Your workload fits on a VPS.** A single site with modest traffic and a database under a few gigabytes does not need a whole chassis. The $79 bracket is the entry point here, and a VPS at a fraction of that covers the same job until you are consistently CPU- or memory-bound.

**You need a GPU or a specific accelerator.** The SpinServers inventory visible today is CPU and SSD storage; GPU capacity is priced separately in this market, with Scaleway quoting €1,274.99/mo for an L40S or H100 machine on a 36-month term and Cherry Servers offering NVIDIA accelerators as a distinct line.

On the way out: Cherry Servers offers a 15-day money-back guarantee on all dedicated plans, provided the terms of service have not been breached. SpinServers does not publish a comparable refund window, and month-to-month rentals in this segment generally do not carry one. If you need an exit ramp, ask in writing before you pay, and get the answer in the ticket.

## Questions buyers ask before the first invoice

**How much should I budget for a dedicated server rental per month?**
Between $25 and $150 covers small to mid-range configurations across most providers. SpinServers sits at $79 for 4 cores and 32GB, or from $235 for 16 cores and 128GB. Above $300 you are buying thread count, memory density or storage, not baseline capability.

**Is the server managed?**
No. Root access and IPMI mean you own the operating system layer. Hardware replacement and network issues are the provider's responsibility; everything above the OS is yours.

**How many IP addresses do I get?**
One IPv4 plus an IPv6 /64 on SpinServers. If you need a block for multiple services, ask about additional addresses at order time, because post-deployment changes are usually slower.

**What happens when I outgrow the machine?**
You migrate to a larger configuration in the same location. Ask whether the provider offers a migration window or a temporary replacement box, since moving a live database between chassis is the part of scaling that hurts.

**How much transfer do I get?**
30TB per month on a 10Gbps port across the SpinServers listings here. Comparable providers quote 50TB or 100TB tiers, or unmetered ports with free inbound traffic under fair use. Check what an overage costs, not just the allowance.

## The decision, in one pass

Single workload, North American audience, monthly billing: take the E3-1280 v5 at $79 and keep the option to walk. Multiple VMs, memory-hungry databases or a virtualization lab: the 128GB dual E5-2630L v3 from $235 is the cheaper route than stacking small machines. Storage server or replication target needing dual 10Gbps and hardware RAID: one of the San Jose configurations, and confirm the RAID card and battery-backed cache before you order. European users, GPU workloads, or anyone who wants a human to manage the OS: rent elsewhere or add a management line to the budget.

Before paying, confirm two things in writing: whether a longer term reduces the price, and whether any refund window exists. 👉 [start with the current SpinServers configurations](https://bit.ly/Spinservers)
