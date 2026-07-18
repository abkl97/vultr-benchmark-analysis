# Is Vultr Worth It? Real Benchmarks and Full Pricing Breakdown — Which Plan Should You Pick? How Does It Compare to DigitalOcean and Linode? Is the $100 Match Promo Legit? (With Setup Guide and Free Credit Codes)

There's a quiet moment most developers hit at some point — the one where you're staring at a cloud provider's pricing page, three tabs open, a spreadsheet filling up next to the coffee cup, and the question forming itself in your head: *"Is Vultr worth it?"*

It's a fair question. Vultr doesn't have the marketing muscle of AWS, the developer cult following of DigitalOcean, or the aggressive European pricing of Hetzner. What it does have is 32 datacenters, a 100% uptime SLA, hourly billing, and a reputation for handing you fast AMD EPYC cores without asking you to take out a mortgage. The catch — and there's always a catch — is in the details. The support tickets. The plan jargon. The "Cloud Compute" vs "Optimized Cloud Compute" vs "High Frequency" maze.

So let's actually walk through this. Not as a sales pitch, not as a teardown, but the way you'd explain it to a friend who's trying to decide where to deploy their next side project or production app.

## Quick Verdict: The Short Version First

If you're in a hurry, here's the honest summary before we dig into the weeds.

| Dimension | Verdict |
| --- | --- |
| **Best for** | Developers who want strong CPU + NVMe disk performance at a fair price; teams with globally distributed users; workloads where transatlantic network throughput matters |
| **Not ideal for** | Teams who need a rich managed-services ecosystem, those who want phone/chat support, or APAC-primary audiences on a tight budget |
| **Entry price** | $2.50/month (IPv6-only) or $5/month (full Cloud Compute) |
| **Uptime SLA** | 100% (network + host node), with credit-backed compensation |
| **Provisioning time** | Under 60 seconds in real testing |
| **Welcome offer** | Vultr Match — deposit $100, get $200 in account credit (code: VULTRMATCH) |
| **Money-back policy** | Strict no-refunds — destroy instances and stop billing, but deposits aren't returned |

That table is the elevator pitch. The rest of this article is the part where you actually decide whether the elevator goes up to your floor.

## What Is Vultr, Really?

Vultr started in 2014 and quietly built a global cloud footprint while everyone else was arguing about Kubernetes on Twitter. By 2026 the company runs 32 datacenters across the Americas, Europe, Asia, Africa, and Australia — from Silicon Valley to Johannesburg, from Delhi to Santiago. The positioning is simple: developer-friendly cloud compute with hourly billing, transparent pricing, and a control panel that doesn't require a PhD to navigate.

What makes Vultr different from the pack isn't any single feature. It's the combination: cheap entry tier, fast AMD EPYC hardware on the High Performance line, generous bandwidth allowances, a one-click app marketplace, and managed services (Kubernetes, databases, object storage, CDN) bolted onto the same billing account. You're not paying for a hyperscaler's worth of services you'll never touch — you're paying for the parts you actually use.

Now, whether that combination is "worth it" depends entirely on what you're building. So let's get specific.

## The Core Question: Is Vultr Worth It? Real Benchmarks

Anyone can claim "high performance." Let's look at what actually happens when you provision a box and run it through its paces. Independent benchmark testing (using the YABS suite on a 2 vCPU / 4 GB Cloud Compute High Performance AMD instance in Silicon Valley) tells a clearer story than any marketing page.

### CPU Performance

The tested instance ran on an AMD EPYC-Genoa processor at 3.25 GHz. Geekbench 6 results:

| Test | Score |
| --- | --- |
| Single Core | 1,926 |
| Multi Core | 3,513 |

For context, that single-core score is roughly 2.5× DigitalOcean's Basic Droplet (772) and about double Hetzner's CPX22 on EPYC-Rome (~939). For CPU-bound workloads — compilation, image processing, latency-sensitive application servers — that's a meaningful gap you'll actually feel, not just a number on a spec sheet.

### Disk I/O

| Block size | Read | Write | Total IOPS |
| --- | --- | --- | --- |
| 4k | 236 MB/s (59k IOPS) | 237 MB/s (59k IOPS) | ~118k combined |
| 64k | 1.83 GB/s | 1.84 GB/s | ~57k IOPS |
| 1m | 2.19 GB/s | 2.33 GB/s | — |

The 4k random IOPS number (~118k combined) is the standout — ahead of both DigitalOcean (54k) and Hetzner CPX22 (40.9k) in equivalent comparisons. Translation: databases, write-heavy logging pipelines, and anything sensitive to disk latency will run noticeably better here.

### Network

A US West Coast server pushing 8.11 Gbits/sec to Amsterdam at 143ms is genuinely impressive. Transatlantic throughput at that level suggests serious upstream peering through major European IXPs. Intra-region (Los Angeles to the tested box) was 9.44ms — tight and predictable.

The honest caveats: IPv6 isn't enabled by default (you tick a box at provisioning), and GPU instances are currently excluded from the SLA due to capacity constraints.

**So is Vultr worth it on performance?** For the price bracket, yes — particularly if your workload is CPU- or disk-intensive. The numbers don't lie, and they're being measured against the actual competitors you're probably comparing it to.

## Pricing and Plans: The Full Landscape

This is where most reviews get vague. Let's not do that. Vultr's lineup splits into two broad buckets — **Shared CPU** (Cloud Compute) and **Dedicated CPU** (Optimized Cloud Compute) — with GPU and Bare Metal tiers stacked on top.

### Cloud Compute (Shared CPU)

The entry-level tier, suitable for low-traffic websites, blogs, CMS, dev/test environments, and small databases. Three sub-flavors:

- **Regular Performance** — older Intel CPUs, standard SSD. Starts at $2.50/month (IPv6-only) or $3.50/month (full).
- **High Performance (AMD or Intel)** — new-generation AMD EPYC or Intel Xeon, NVMe SSD. Starts at $6/month for 1 vCPU / 1 GB / 25 GB NVMe.
- **High Frequency** — 3GHz+ Intel Xeon, NVMe. Starts at $6/month for 1 vCPU / 1 GB / 32 GB NVMe.

### Optimized Cloud Compute (Dedicated CPU)

These run on fully dedicated, new-generation AMD EPYC vCPUs. Four plan types depending on what you're optimizing for:

- **General Purpose** — balanced CPU/RAM/NVMe. Web servers, e-commerce, game servers, video streaming, APIs. Starts at $28/month (1 vCPU / 2 GB) on the CPU-Optimized end, or $30/month for General Purpose (1 vCPU / 4 GB).
- **CPU Optimized** — proportionally more CPU. Video encoding, CI/CD, batch processing, HPC, ad serving. Starts at $28/month.
- **Memory Optimized** — proportionally more RAM. MySQL, Memcached, real-time analytics. Starts at $40/month.
- **Storage Optimized** — large NVMe volumes. Cassandra, MongoDB, high-frequency OLTP. Starts at $75/month.

There's also the newer **VX1** tier — Vultr's price-to-performance efficiency line, claiming up to 82% better performance per dollar vs. hyperscaler cost-optimized instances, with up to 50 Gbps networking and provisioning in under 15 seconds. Starts at $43.80/month.

### Cloud GPU

For AI/ML workloads, Vultr offers fractional, full, or multiple NVIDIA GPUs:

- **NVIDIA GH200** — $2,913/month ($4.335/hr) for 1 GPU, 96 GB GPU RAM, 72 vCPUs, 480 GB RAM
- **NVIDIA H100** — $13,432/month ($19.988/hr) for 8 GPUs, 640 GB GPU RAM, 224 vCPUs, 2048 GB RAM
- **NVIDIA A100** — starting at $0.134/hr
- **NVIDIA L40S** — starting at $2.604/hr
- **NVIDIA A40** — starting at $0.082/hr
- **NVIDIA A16** — starting at $0.033/hr

### Bare Metal

Single-tenant dedicated servers with NVIDIA GPU options, starting around $3.500/GPU/hour for premium configurations.

## Full Plan Comparison Table

Below is the consolidated view of Vultr's main Cloud Compute and Optimized Cloud Compute tiers. Every plan currently displayed on the official pricing page is included — nothing omitted.

| Plan Family | Specs (Entry) | Storage | Bandwidth | Price (Monthly) | Hourly |  Get Started |
| --- | --- | --- | --- | --- | --- | --- |
| Cloud Compute — Regular (IPv6 only) | 1 vCPU / 0.5 GB | 10 GB SSD | 0.5 TB | $2.50 | $0.004 |  [Claim $100 Match Credit](https://www.vultr.com/?ref=9738262-9J) |
| Cloud Compute — Regular | 1 vCPU / 0.5 GB | 10 GB SSD | 0.5 TB | $3.50 | $0.005 |  [Claim $100 Match Credit](https://www.vultr.com/?ref=9738262-9J) |
| Cloud Compute — Regular | 1 vCPU / 1 GB | 25 GB SSD | 1 TB | $5 | $0.007 |  [Claim $100 Match Credit](https://www.vultr.com/?ref=9738262-9J) |
| Cloud Compute — High Performance AMD | 1 vCPU / 1 GB | 25 GB NVMe | 2 TB | $6 | $0.009 |  [Deploy High Performance AMD](https://www.vultr.com/products/cloud-compute/?ref=9738262-9J) |
| Cloud Compute — High Performance AMD | 2 vCPU / 4 GB | 100 GB NVMe | 5 TB | $24 | $0.036 |  [Deploy High Performance AMD](https://www.vultr.com/products/cloud-compute/?ref=9738262-9J) |
| Cloud Compute — High Performance AMD | 8 vCPU / 16 GB | 350 GB NVMe | 8 TB | $96 | $0.143 |  [Deploy High Performance AMD](https://www.vultr.com/products/cloud-compute/?ref=9738262-9J) |
| Cloud Compute — High Frequency | 1 vCPU / 1 GB | 32 GB NVMe | 1 TB | $6 | $0.009 |  [Deploy High Frequency](https://www.vultr.com/products/cloud-compute/?ref=9738262-9J) |
| Cloud Compute — High Frequency | 2 vCPU / 4 GB | 128 GB NVMe | 3 TB | $24 | $0.036 |  [Deploy High Frequency](https://www.vultr.com/products/cloud-compute/?ref=9738262-9J) |
| Cloud Compute — High Frequency | 12 vCPU / 48 GB | 768 GB NVMe | 8 TB | $256 | $0.381 |  [Deploy High Frequency](https://www.vultr.com/products/cloud-compute/?ref=9738262-9J) |
| Optimized — General Purpose | 1 vCPU / 4 GB | 30 GB NVMe | 4 TB | $30 | $0.045 |  [Deploy General Purpose](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — General Purpose | 4 vCPU / 16 GB | 80 GB NVMe | 6 TB | $120 | $0.179 |  [Deploy General Purpose](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — General Purpose | 96 vCPU / 256 GB | 1280 GB NVMe | 12 TB | $3,840 | $5.714 |  [Deploy General Purpose](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — CPU Optimized | 1 vCPU / 2 GB | 25 GB NVMe | 4 TB | $28 | $0.042 |  [Deploy CPU Optimized](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — CPU Optimized | 8 vCPU / 16 GB | 300 GB NVMe | 7 TB | $180 | $0.268 |  [Deploy CPU Optimized](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — Memory Optimized | 1 vCPU / 8 GB | 50 GB NVMe | 5 TB | $40 | $0.060 |  [Deploy Memory Optimized](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — Memory Optimized | 16 vCPU / 128 GB | 3200 GB NVMe | 10 TB | $1,000 | $1.488 |  [Deploy Memory Optimized](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — Storage Optimized | 1 vCPU / 8 GB | 150 GB NVMe | 4 TB | $75 | $0.112 |  [Deploy Storage Optimized](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Optimized — Storage Optimized | 32 vCPU / 256 GB | 5760 GB NVMe | 12 TB | $2,000 | $2.976 |  [Deploy Storage Optimized](https://www.vultr.com/products/optimized-cloud-compute/?ref=9738262-9J) |
| Cloud GPU — NVIDIA GH200 | 1 GPU / 72 vCPU / 480 GB | 4800 GB | 25 TB | $2,913 | $4.335 |  [Deploy GH200](https://www.vultr.com/products/cloud-gpu/?ref=9738262-9J) |
| Cloud GPU — NVIDIA H100 | 8 GPU / 224 vCPU / 2048 GB | 32640 GB | 15 TB | $13,432 | $19.988 |  [Deploy H100](https://www.vultr.com/products/cloud-gpu/?ref=9738262-9J) |
| Bare Metal | Single-tenant dedicated | Configurable | Configurable | From ~$750 | $1.042 |  [Deploy Bare Metal](https://www.vultr.com/products/bare-metal/?ref=9738262-9J) |

> **Pricing note:** Cloud Compute and High Performance plans are billed hourly and capped at 672 hours/month — meaning a server running a full 31-day month costs the same as 28 days. The VX1 tier is the exception: it bills on actual hours in the month. Pricing can vary slightly by datacenter region. Overages beyond included bandwidth are billed at $0.01/GB.

## The Match Promo: Is the $100 Free Credit Legit?

This is one of the questions people actually search for, so let's address it directly.

Vultr runs a recurring promotion called **Vultr Match**. The mechanics are simple: when you create a new account and make your first credit deposit, Vultr matches it dollar-for-dollar up to $100. Deposit $100, you get $200 in account balance. Use code **VULTRMATCH** at signup.

There are also separate free-credit offers floating around (codes like **FLYTWOHUNDRED** for $200 free credit and **FLY300VULTR** for $300 free credit) — these tend to be time-limited and tied to specific promotional windows, so check the official coupons page for what's currently live.

The fine print matters here:

- Match credit is applied on a **50/50 basis** — if your hourly accrued balance is $10, $5 comes from promotional credit and $5 from your real funds.
- Match credit expires **12 months** after issuance.
- The match promotion is only for **new customers** — existing accounts and duplicate accounts are not eligible.
- Free-credit promotional codes typically expire in **30 days**, so plan your testing window accordingly.

Is the promo "legit"? Yes — but treat it as a **trial runway**, not a permanent discount. It's a genuinely useful way to benchmark Vultr on your actual workload before committing real money. 👉 [You can grab the Match promo and start a free trial here](https://www.vultr.com/?ref=9738262-9J).

## Real User Reviews: What People Actually Say

Marketing pages tell you what a company wants you to hear. Review aggregators tell you what angry people shout about. The truth is somewhere in the middle. Here's the honest composite from G2, Capterra, Trustpilot, Reddit, and Software Advice.

### What Users Praise

- **Ease of use and transparent pricing** — repeatedly highlighted in G2 reviews. Server deployment in under a minute, no surprise line items on the invoice.
- **Speed and reliability for the price** — "99% uptime with great speed performance" is a common refrain. The AMD EPYC hardware genuinely delivers.
- **Cheap, simple, fast UI** — straight from Reddit's webhosting community. "I recommend Vultr to everyone. Cheap, simple and fast UI, reliable so far."
- **Cost savings vs. hyperscalers** — multiple TrustRadius reviewers cite Vultr as 20–40% cheaper than DigitalOcean and dramatically cheaper than AWS/GCP for equivalent specs.
- **Generous bandwidth allowances** — the included monthly transfer is more forgiving than most competitors at this tier.

### What Users Complain About

- **Customer support responsiveness** — the most consistent negative theme across Trustpilot. Slow responses, generic fixes, escalation paths that feel opaque. (One direct test by an independent reviewer did get a 10-minute reply on a Monday morning, so experiences vary widely.)
- **Account termination without notice** — a recurring complaint, particularly from users who apparently tripped automated abuse thresholds. Read the acceptable use policy carefully.
- **No refunds policy** — deposits are non-refundable. If you fund your account with $200 and decide to leave, you can stop the billing bleeding but you won't get the unused balance back.
- **Shared-CPU throttling under sustained load** — Vultr will resource-limit VPS instances that consistently hammer the host node, with a polite suggestion to upgrade to Dedicated or Bare Metal. Reasonable from their side, jarring if you didn't see it coming.
- **Object storage reliability** — a handful of reports of intermittent issues, with support responses that feel low-urgency.

### The Composite Picture

If you read the praise and the complaints side by side, a coherent profile emerges. Vultr is **excellent on hardware, pricing, and deployment speed**. It is **mediocre on support, refunds, and edge-case reliability**. The people who love Vultr are developers who don't need to call support. The people who hate Vultr are the ones who needed to call support at 2 AM and didn't get the answer they wanted.

## Who Should (and Shouldn't) Use Vultr

This is the question that actually matters. Let me be specific.

### Vultr Is Worth It If You Are…

- A **developer or small team** deploying web apps, APIs, or databases where you want fast provisioning and clean hourly billing.
- Running **CPU- or disk-intensive workloads** — compilation, image processing, databases — where the AMD EPYC + NVMe combo actually moves the needle.
- Serving a **globally distributed audience** and need 32 datacenter locations to keep latency low.
- Comfortable with **command-line server administration** and don't expect managed-support handholding.
- Building **AI/ML workloads** and want GPU access (H100, GH200, A100) without AWS's pricing complexity.
- Running **e-commerce** and want the 640 GB SSD Cloud Compute instance (8 vCPU / 32 GB RAM / 6 TB bandwidth) — a sweet spot for mid-traffic stores.

### Vultr Is Probably Not Worth It If You Are…

- A **complete beginner** who expects a cPanel-style managed hosting experience with 24/7 phone support.
- A team that needs a **rich managed-services ecosystem** — DigitalOcean's App Platform, AWS's full PaaS suite, or Vercel/Netlify-style frictionless deploys are better fits.
- Primarily serving **APAC audiences on a tight budget** — Hetzner's Asian expansion and local providers may undercut on price.
- An organization that requires **SOC 2, HIPAA, ISO 27001, or PCI DSS compliance** baked into the contract — Vultr has some certifications but competitors like Linode (Akamai) have a more complete compliance story.
- Someone who will be **deeply unhappy if you can't get a refund** when things go sideways.

## Setup Experience: What It Actually Feels Like

Here's the part most reviews skip — the actual flow of getting a server running.

Vultr splits provisioning across two screens, which is a deliberate design choice. **Page one** is hardware and location: you pick Shared CPU or Dedicated CPU, then a datacenter from the 32-location grid (filterable by region, with an "Available Services" indicator confirming what's actually deployable in that zone before you commit). Then you pick a plan family — VX1, General Purpose, CPU Optimized, Memory Optimized, Storage Optimized — with a live summary panel showing vCPUs, RAM, storage, and hourly price as you toggle.

**Page two** is software and deployment: OS image (Ubuntu, Debian, Fedora, Rocky, AlmaLinux, FreeBSD, and others, plus a one-click marketplace with WordPress, Docker, LAMP, cPanel, and more), SSH keys (saved keys appear automatically with a checkbox), optional add-ons (automated backups, DDoS protection, IPv6), and startup scripts.

Provisioning completes in under 60 seconds on tested instances. The instance detail page surfaces power controls, bandwidth graphs, a browser-based console (useful if a firewall misconfiguration locks you out of SSH), snapshot management, and block storage attachment.

The control panel is functional without being beautiful. It's the kind of interface you stop noticing after a week — which, frankly, is the highest compliment you can pay infrastructure UI.

## The Ecosystem: Beyond Plain Compute

Vultr has steadily built out managed services around the compute core. Worth knowing about:

- **Managed Databases** — MySQL, PostgreSQL, Valkey (the Redis-compatible fork), and Apache Kafka. Automated backups, standby replicas, connection pooling. PostgreSQL clusters start at $15/month on standard compute.
- **Vultr Kubernetes Engine (VKE)** — auto-scaling node pools, integrated load balancers, container registry. The control plane is free; you pay only for worker nodes.
- **Object Storage** — S3-compatible, four performance tiers starting at $18/month for Standard ($0.018/GB additional).
- **Block Storage** — NVMe at $0.10/GB/month, attachable to any running instance.
- **File System** — shared NVMe storage at $100/TB/month for multi-instance workloads.
- **CDN** — built-in push and pull zones for static asset delivery.

The honest take: Vultr's managed services are competent but not best-in-class. If you're already invested in AWS's RDS or DigitalOcean's App Platform, Vultr's equivalents won't pull you across. But if you're starting fresh and want one billing account for everything, the integrated stack is a real convenience.

## Is Vultr Worth It Compared to DigitalOcean and Linode?

Since "is Vultr worth it" usually means "is Vultr worth it instead of DigitalOcean or Linode," let's address the head-to-head.

| Dimension | Vultr | DigitalOcean | Linode (Akamai) |
| --- | --- | --- | --- |
| **Entry price** | $2.50/mo (IPv6) / $5/mo | $4/mo | $5/mo |
| **Datacenters** | 32 | 14 | 11+ |
| **Uptime SLA** | 100% | 99.99% | 99.9% |
| **CPU (single-core, Geekbench 6)** | ~1,926 (AMD EPYC) | ~772 (Basic Droplet) | varies |
| **4k IOPS** | ~118k combined | ~54k | varies |
| **Managed Kubernetes** | Free control plane | Free control plane | Paid |
| **Free trial credit** | $100 Match + up to $300 codes | $200 | $100 |
| **Best for** | Performance-per-dollar, global reach | Developer ecosystem, managed services | Compliance, stability |

The pattern: **Vultr wins on raw hardware performance and datacenter reach**. DigitalOcean wins on developer ecosystem polish. Linode wins on compliance certifications and the stability that comes from being owned by Akamai. None of them is strictly "better" — they're optimized for different buyers.

If you care most about price-to-performance on a 2 vCPU / 4 GB instance, Vultr's $24/month High Performance AMD box is genuinely the strongest spec in this peer group. If you care most about managed services and one-click everything, DigitalOcean. If compliance is your bottleneck, Linode.

## Final Verdict: So, Is Vultr Worth It?

Here's the honest, no-hand-waving answer.

**Vultr is worth it** for developers and small-to-medium teams who want fast AMD EPYC hardware, generous NVMe disk performance, 32 global datacenters, and clean hourly billing — and who don't need hand-holding from support. The price-to-performance ratio is real, the benchmarks back it up, and the $100 Match promo gives you a no-risk runway to test it on your actual workload.

**Vultr is not worth it** if you need enterprise-grade support, refund flexibility, a rich PaaS ecosystem, or you're a complete beginner who expects managed hosting. The no-refunds policy and the occasional shared-CPU throttling are real trade-offs.

The question "is Vultr worth it" is really asking "is Vultr worth it for *me*?" — and the answer depends almost entirely on whether you're the kind of operator who reads the docs before opening a ticket, or the kind who expects the host to read them for you.

If you're the first kind, 👉 [grab the $100 Match credit and try it on your own workload](https://www.vultr.com/?ref=9738262-9J) — that's the only way to actually answer the question for your specific use case.

## FAQ: The Questions People Actually Ask

**Is Vultr good for beginners?**
Not really. The control panel is cleaner than most cloud providers, and one-click installers help, but you're still configuring and deploying instances yourself. If you want fully managed hosting with cPanel and 24/7 support, look elsewhere. If you're willing to learn, the docs are solid.

**Does Vultr have a free trial?**
Yes — through promotional credit codes. The **VULTRMATCH** code matches your first deposit up to $100, giving you $200 in account balance. Time-limited codes for $200–$300 in free credit also circulate periodically. Check the official coupons page for what's currently active.

**Is Vultr cheaper than AWS?**
Significantly. For equivalent specs, Vultr is typically 30–60% cheaper than AWS on-demand pricing, with simpler billing and no EBS/IOPS surprise charges.

**Can I get a refund from Vultr?**
No. Vultr has a strict no-refunds policy. You can destroy instances to stop billing, but unused account balances are not returned. Fund only what you intend to use.

**Which Vultr plan is best for a small website?**
The $5/month Cloud Compute Regular plan (1 vCPU / 1 GB / 25 GB SSD / 1 TB bandwidth) handles low-traffic WordPress sites, blogs, and small apps comfortably. Upgrade to High Performance ($6/month) if you want NVMe and newer CPUs.

**Which Vultr plan is best for e-commerce?**
The 8 vCPU / 32 GB / 640 GB SSD Cloud Compute instance ($160/month) is a strong mid-tier choice. For NVMe performance, the High Performance equivalent at $96/month (8 vCPU / 16 GB / 350 GB NVMe) is also worth considering depending on your storage needs.

**Does Vultr support GPU workloads?**
Yes — NVIDIA GH200, H100, A100, L40S, A40, and A16 are all available, plus AMD accelerators. Pricing starts at $0.033/hour for entry-level GPUs and scales to $19.988/hour for 8× H100 configurations.

**Is Vultr's uptime SLA real?**
Vultr offers a 100% uptime SLA covering network and host node availability, with credit-backed compensation for downtime. GPU instances are currently excluded from the SLA due to capacity constraints.
