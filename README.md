# Unmanaged VPS Server: What You Own, What Support Covers, and How to Size One (Spin Servers' Six KVM Tiers Compared)

An unmanaged VPS server hands you four jobs that managed hosting quietly absorbs: OS and control-panel updates, monitoring, security patching, and backups. What you get in return is the one thing managed plans don't give out, full root access. Everything below the operating system, meaning the hardware, power, network and the data centre itself, stays with the provider.

Below is the work split in a single table, the places where "unmanaged" stops meaning the same thing from one host to the next, Spin Servers' current KVM VPS lineup and what its published SLA actually promises, and the sizing rules that decide which tier you need.

> **Quick pick:** one production site or a handful of containers fits the 6 vCPU / 8 GB tier Spin Servers lists from **$39.00 USD per month**. Take 2 vCPU / 2 GB for staging, CI or a side project, and move to 16 vCPU / 16 GB only when RAM is what you keep exhausting, not core count.
> 👉 [See Spin Servers' current KVM VPS plans and pricing](https://bit.ly/Spinservers)

## The work split, without the marketing

Hosts that sell both products publish roughly the same comparison, and the pattern is consistent: the hardware layer is theirs on both plans, the software layer is yours only on unmanaged.

| Job | Unmanaged VPS | Managed VPS |
| --- | --- | --- |
| Full root access | Yes | No |
| Your choice of Linux distribution | Yes | No |
| Datacenter power and network | Provider | Provider |
| Dual power/network uplinks, RAID storage | Provider | Provider |
| OS and control-panel updates | You | Provider |
| Monitoring (CPU, disk, uptime) | You | Provider |
| Security patching | You | Provider |
| Proactive support from an on-call engineer | No | Yes |
| Backups | Optional add-on | Usually daily, included |
| Hardware and network SLA | Typically 99.9% | Typically 99.95% or higher |

Two rows matter more than the rest. Root access exists only on the unmanaged side; if a provider offers managed VPS, it will not hand you root. And backups are an add-on, not a default. hosting.com puts it plainly on its own product page: you handle "your own backups unless you add ours." Budget for that line item or run your own snapshots to object storage from day one.

The same page draws the buyer line clearly. If you are coming off shared hosting and want to keep an intuitive panel like cPanel, take managed. If you are comfortable on the command line and want root so you can customise the server, take unmanaged. Buying unmanaged to save $10 and then discovering you wanted cPanel is the most common way this decision goes wrong.

## "Unmanaged" still means somebody is watching the hardware

The word gets used loosely. Hostwinds states that its unmanaged Linux VPS plans "do not come with any technical, management, or administrative support," and that the company only ensures the VPS can start up with power, networking and connectivity between your server and its backend. That is the strictest reading you will find: infrastructure only.

Then the same provider says it runs a real-time monitoring service on all VPS plans and automatically opens a support ticket when it detects a technical issue. So "no support" and "no monitoring" are separate promises. A host can refuse to debug your nginx config while still noticing at 3 a.m. that your node stopped responding.

Support hours are where the real spread shows up. Liquid Web's write-up on unmanaged VPS notes that some hosts offer only very basic support, and that at least one provider restricts standard and premium customers to working-hours support, which it calls a way to be left "high and dry" during an outage. The same piece flags a provider whose cheapest plan ships with no automated backups.

For Spin Servers, the SLA page is worth reading before you buy rather than after. It states that dedicated servers are unmanaged unless otherwise stated, and that the uptime commitment covers network and power availability, plus replacement of failed components the company supplied: processors, memory, drives, network interfaces, power supplies and fans. The scope statement names dedicated server and colocation services. A KVM VPS is not named in it. If a written uptime guarantee is part of why you are buying, get the coverage confirmed for the VPS line in a ticket before you pay, and keep the reply.

## Spin Servers' KVM VPS lineup

The VPS catalogue is a KVM line sold by the slice: you pick the size, you get RAID-10 SSD storage, a 1 Gbps port, one IPv4 and one IPv6 address, and a monthly transfer allowance that grows with the plan. Third-party tracking of the brand lists root access as included and no managed tier, which matches how the product is sold: assume you are the administrator.

| Plan | vCPU / RAM | Storage · monthly transfer | Price (USD, monthly) | Order |
| --- | --- | --- | --- | --- |
| Simple Application Server (Intel) | 2 vCPU / 2 GB DDR4 | 40 GB RAID-10 SSD · 4 TB | Quoted on order page | [ Order](https://bit.ly/Spinservers) |
| KVM 6vCPU 8GB (featured) | 6 vCPU / 8 GB DDR4 | 120 GB RAID-10 SSD · 8 TB | **$39.00** | [ Order](https://bit.ly/Spinservers) |
| KVM 8vCPU 8GB | 8 vCPU / 8 GB DDR4 | 160 GB RAID-10 SSD · 10 TB | Quoted on order page | [ Order](https://bit.ly/Spinservers) |
| KVM 12vCPU 12GB | 12 vCPU / 12 GB DDR4 | 160 GB RAID-10 SSD · 10 TB | Quoted on order page | [ Order](https://bit.ly/Spinservers) |
| Simple Application Server (Intel Xeon) | 16 vCPU / 16 GB DDR4 | 320 GB RAID-10 SSD · 15 TB | Quoted on order page | [ Order](https://bit.ly/Spinservers) |
| Advanced Application Server (Intel Xeon) | 32 vCPU / 32 GB | 500 GB SSD · 20 TB | Quoted on order page | [ Order](https://bit.ly/Spinservers) |

The 6 vCPU / 8 GB tier is the only one with a publicly listed starting price. The rest are priced per tier on the order page, so treat those cells as "go look" rather than a quote. 👉 [Open the Spin Servers VPS order page to price each tier](https://bit.ly/Spinservers)

Read the specs as a ladder and one rung looks odd. Going from 6 vCPU to 8 vCPU keeps you at 8 GB of RAM and adds 40 GB of disk and 2 TB of transfer. If your workload is already swapping at 8 GB, that upgrade buys you nothing: you get more cores to wait on the same memory. The 12 vCPU / 12 GB step is the one that actually moves memory, and it keeps the 160 GB of storage the 8 vCPU tier already had.

Two details on the same page that affect what you can run:

- **Port 25 is closed by default on every VPS.** Spin Servers says it does this to limit IP abuse, and that you can request the port be opened via a ticket with a justification. The company reserves the right to refuse. If a mail server is part of the plan, that is a dependency to resolve before you migrate, not after.
- **The plan names are honest about positioning.** The 2 vCPU tier is labelled Simple Application Server, and the 32 vCPU tier is labelled Advanced Application Server rather than KVM. Same product family, different intended workload.

## What the uptime credit actually pays out

Spin Servers publishes a credit table for its dedicated commitment: 99.99% monthly uptime or better earns nothing, 99.95% to below 99.99% earns a 10% credit, and the scale steps to 20%, 30% and 40% as availability falls below 99.80%. Service credits are calculated on the monthly recurring charge of the affected service.

Three conditions in the same document change how much that is worth:

- Credits are **not cash refunds** and cannot exceed the monthly recurring charge for the affected service.
- Exclusions include scheduled or emergency maintenance with reasonable notice, customer-owned equipment, software, operating systems, cabling or configurations, customer actions, suspension for nonpayment or abuse, DDoS attacks and traffic filtering done to protect the network, and events outside the company's reasonable control.
- You have to claim it. Open a ticket through the client portal after the incident, with the affected service and approximate start and end times.

For context on why the credit matters less than the outage: downtime cost figures circulating in the industry, including the widely quoted $9,000 per minute that Liquid Web cites from Pingdom's outage research, are second-hand. Treat them as an order of magnitude, not a number to put in a budget. The practical point stands: a 40% credit on a $39 month does not cover a day of lost orders.

## Sizing rules by scenario

- **Staging, CI runner, a personal site, a small side project.** 2 vCPU / 2 GB with 40 GB of disk. Nothing on this list is cheaper, and nothing else is close to appropriate for a box you rebuild weekly.
- **One production site with a database, a few containers, a queue worker.** 6 vCPU / 8 GB at $39.00 USD monthly. This is the tier where the price is published and the specs are balanced, and for most readers asking about an unmanaged VPS server it is the answer.
- **JVM services, Elasticsearch, Postgres with a working set of several GB.** 16 vCPU / 16 GB with 320 GB of RAID-10. You are buying memory and disk headroom here, and the extra cores are a side effect.
- **Build farms, transcoding, many small containers.** 32 vCPU / 32 GB. One GB of RAM per vCPU is thin for anything memory-hungry, so this tier rewards parallel CPU work and punishes badly behaved Java heaps.
- **You want cPanel and someone else to patch.** None of the above. Buy managed VPS. The money you save on an unmanaged plan is the money you are paying yourself to be the sysadmin, and that trade only works if you would actually do the work.

## The costs that aren't in the plan table

The sticker price is the CPU, RAM, disk, transfer, port and IPs. Four other things decide your real monthly number.

**Backups.** They are not in the KVM spec list. Either run your own (snapshots to object storage, a database dump cron, whatever you already trust) or ask what a backup add-on costs. A provider that includes nightly backups to its own object storage and lets you restore a single file is offering something meaningfully different from "you have RAID."

**Control panel licences.** cPanel and Plesk are almost always billed separately from the server. Liquid Web, for example, includes InterWorx free but charges monthly for Plesk and cPanel; hosting.com sells cPanel as an add-on running on AlmaLinux. If your stack assumes a panel, price the licence before you compare two VPS quotes as if they were equivalent.

**Your hours.** Patching, monitoring alerts, certificate renewals, the 2 a.m. page. This is the actual product you are buying when you choose unmanaged.

**Upgrade mechanics.** With most hosts you resize from the control panel, the change takes effect within minutes, and there is no migration or downtime. If that matters, confirm it for your specific provider, because the alternative (rebuild and migrate) turns a $20 upgrade into a weekend.

## FAQ

**Does an unmanaged VPS include technical support?**
At the strictest end, no: Hostwinds guarantees only that the VPS starts and has power, networking and connectivity, and says it supplies no other assistance. Other hosts will answer infrastructure tickets and monitor the node but stop at your application. Ask what response times you get and during which hours before you buy, because "24/7 chat" and "24/7 technical support" are different products.

**Can I upgrade to a managed plan later?**
At some hosts yes, with one click in the control panel, and 24/7 support applies once the upgrade completes. If you think you might want that exit, confirm the provider offers a managed tier at all. A host with no managed product leaves you migrating to a different company.

**Can I reinstall or switch the OS?**
On self-managed KVM plans, generally yes, from the control panel, whenever you need. That is one of the concrete advantages of the model: a broken box is a 20-minute rebuild, not a support ticket and an argument.

**How long does pointing a domain at the server take?**
Change the A record to the VPS IP. Propagation usually takes a few hours and can take up to 72.

**Can I run Windows?**
Some hosts sell a separate unmanaged Windows VPS line, so the capability exists in the market. Spin Servers' VPS page is built around Linux-shaped application servers, so confirm the OS template list in a ticket before you assume Windows is available.

## Before you order

Three questions, all answerable in a pre-sales ticket, all worth asking before money changes hands:

1. Are backups included, and if not, what does the add-on cost per month?
2. Does the SLA cover this VPS product, and what exactly does it compensate: power and network only, or the server too?
3. What does support cover on this plan, during which hours, and what is the refund or cancellation window?

Then pick by workload, not by tier name. Staging and side projects: 2 vCPU / 2 GB. One production site with a database, or a small container fleet: 6 vCPU / 8 GB at $39.00 USD monthly. Memory-bound services: 16 vCPU / 16 GB. Parallel CPU work: 32 vCPU / 32 GB, with your eyes open about 1 GB of RAM per core. Anyone who wants a panel and patching handled should skip this whole category and buy managed.

👉 [Check Spin Servers' KVM VPS tiers and current pricing](https://bit.ly/Spinservers)
