# VPS cheap for blog hosting: what $50 a year buys you, how to set up WordPress, and when to spend more

A blog does not need much of a server. That sentence annoys hosting companies that sell $25/month managed plans, but it holds up under basic math, and it explains why so many bloggers end up searching for a cheap VPS instead. You get a full Linux server, root access, no noisy neighbors on shared hosting, and — if you pick the right provider — a bill that costs less per year than one month of a premium managed host.

The catch is that "cheap VPS" covers everything from $4/month cloud instances to $90/month premium boxes, and the cheapest option is not automatically the right one for a blog. This guide walks through what a blog actually consumes, where BandwagonHost fits into the cheap-VPS landscape with its current plans and prices, what self-managed hosting really demands from you, and how to get a WordPress site running without paying for things you will never use.

## What "cheap" means for a blog VPS right now

Look at the current market and you find three distinct price bands.

Shared hosting marketed to bloggers runs $2–$10/month, but you are renting a slice of a crowded machine with hard CPU limits. Managed WordPress VPS plans from the big names run roughly $10–$35/month once you factor in renewals — the reviews consistently note that the promotional price is not the renewal price. And then there is the unmanaged VPS tier, where entry cloud instances from DigitalOcean or Vultr sit around $4–$6/month, and specialty budget providers go lower on annual billing.

BandwagonHost operates in that last tier, aggressively. Its entry **20G KVM plan costs $49.99 per year**, which works out to about $4.17 a month — with annual billing, so no surprise renewal hike, and no teaser rate that doubles after year one.

The reason the price is real rather than a bait-and-switch is the business model: the service is strictly self-managed. BandwagonHost (operated by IT7 Networks) handles the hardware, network, power and hypervisor; everything from the operating system up is yours. That trade is the entire reason a $4/month server can exist. It is also the first filter you should apply — if you want someone to answer tickets about your wp-config.php file, an unmanaged VPS is the wrong category entirely.

## First, size your blog (it is probably smaller than you think)

Before comparing plans, work out what a blog actually consumes, because the numbers are humbling.

**Traffic.** A cached WordPress page runs roughly 0.5–2 MB per visit in practice. The entry BandwagonHost plan includes 1 TB of monthly transfer, which at those sizes covers somewhere in the neighborhood of half a million to two million pageviews a month. If your blog does a fraction of that, you are not bandwidth-constrained, and you will not be for years.

**RAM.** The entry plan ships 1 GB. A lean WordPress stack — lightweight theme, a caching plugin, Redis or even just page caching, and no page-builder bloat — fits in 1 GB comfortably for a single site. The classic failure mode is not traffic; it is a 60-plugin lineup and an unoptimized database.

**CPU.** Static page serving after caching barely registers. The 20G plan's two Xeon cores are doing real work only during cache misses and admin tasks.

There is an honest counterpoint: if your "blog" is really an image portfolio, a membership site, or a WooCommerce shop, the calculus shifts and 2 GB of RAM starts looking like the sensible floor. That is what the 40G plan is for. But for text-and-images blogging, the entry spec is not a compromise; it is the actual requirement, sold in its smallest wrapper.

## BandwagonHost's current plans and prices

The core lineup on the VPS hosting page is a ladder of six self-managed KVM plans, all on SSD RAID-10 storage with 1 Gbit ports, deployable across multiple datacenters (Los Angeles, New York, Fremont, New Jersey, Vancouver, Amsterdam, among others) with **free migration between locations at any time**. Every plan in the table includes free automatic backups, free snapshots, one dedicated IPv4, a routed /64 IPv6 subnet, full root access, and a 99.95% uptime guarantee.

| Plan | SSD (RAID-10) | RAM | CPU | Transfer | Starting price | Billing |
| --- | --- | --- | --- | --- | --- | --- |
| 20G KVM | 20 GB | 1 GB | 2x Intel Xeon | 1 TB/mo | **$49.99 USD** | annually |
| 40G KVM | 40 GB | 2 GB | 3x Intel Xeon | 2 TB/mo | $52.99 USD | semi-annually ($99.99/yr) |
| 80G KVM | 80 GB | 4 GB | 4x Intel Xeon | 3 TB/mo | $19.99 USD | monthly ($199.99/yr) |
| 160G KVM | 160 GB | 8 GB | 5x Intel Xeon | 4 TB/mo | $39.99 USD | monthly ($399.99/yr) |
| 320G KVM | 320 GB | 16 GB | 6x Intel Xeon | 5 TB/mo | $79.99 USD | monthly ($799.99/yr) |
| 480G KVM | 480 GB | 24 GB | 7x Intel Xeon | 6 TB/mo | $119.99 USD | monthly ($1,199.99/yr) |

For a single blog, the decision is nearly always between the first two rows. The 20G plan is the one that made this provider famous in budget-hosting circles: 1 GB RAM, 20 GB SSD, 1 TB traffic, about $4 a month. If you want more headroom for plugins or a second lightweight site on the same box, the 40G plan doubles nearly everything — its annual price of $99.99 is the better per-year deal than paying the semi-annual rate twice.

👉 [查看最新的 20G KVM 年付价格](https://bit.ly/BandwagonHost)

### The premium lines, in one honest paragraph

BandwagonHost also sells a range of network-optimized plans, and you will see them mentioned in every review, so here is the short version: they exist for people whose audience sits behind mainland-China networks. The regular routes into China (the ones every ordinary cloud provider uses) get congested at peak hours, with packet loss that can reach 30% or worse; the CN2 GIA and CTGNet routes are premium, stable alternatives that the provider runs on 8x10 Gbe links out of Los Angeles, with China-bound traffic carried over China Telecom CN2 GIA, China Mobile CMIN2, and China Unicom Premium simultaneously.

For a blog with a mostly Western audience, these plans are irrelevant. For a blog whose readers are in China, they are the entire point. The entry CN2 GIA-E plan has been listed at **$49.99/quarter or $169.99/year** (2 cores, 1 GB RAM, 20 GB SSD, 1 TB traffic, 2.5 Gbps port), and it rotates in and out of stock. The premium line-up goes up from there:

| Product family | Entry config | Entry price | Best for |
| --- | --- | --- | --- |
| CN2 GIA-E (LA DC9, Osaka, etc.) | 1 GB / 20 GB / 1 TB | $49.99 quarterly · $169.99 yearly | Stable China access without HK prices |
| E-Commerce SLA Los Angeles (99.99% SLA) | 1 GB ECC / 20 GB NVMe / 1 TB | $65.89 quarterly · $239.99 yearly | Business sites needing an SLA |
| Osaka CN2 GIA (Equinix) | 2 GB / 40 GB / 500 GB | $49.99 monthly · $499.99 yearly | Japan low-latency |
| Singapore CN2 GIA (Equinix SG1) | 2 GB / 40 GB / 500 GB | $49.99 monthly · $499.99 yearly | SE Asia low-latency |
| Hong Kong CN2 GIA (Equinix HK2) | 2 GB / 40 GB / 500 GB | $89.99 monthly · $899.99 yearly | Lowest China latency, no budget |
| Tokyo CN2 GIA (Equinix TY8) | 2 GB / 40 GB / 500 GB | $89.99 monthly · $899.99 yearly | Same, Tokyo flavor |

The pattern to notice: identical-looking specs can differ by 10x in price, and the difference is routing and facility cost, not compute. A blog almost never needs to pay it.

👉 [比较 CN2 GIA-E 与 SLA 套餐的完整配置](https://bit.ly/BandwagonHost)

## What self-managed actually means day to day

The provider's own site says it plainly: the service is self-managed, and that is what keeps the price down. Translated into a normal week of running a blog, here is the deal.

You get the KiwiVM control panel, built in-house, which handles the genuinely annoying parts of VPS life: one-click OS reloads, an emergency console for when you lock yourself out, rDNS management, usage statistics, an API, and — the feature users praise most — **free one-click datacenter migration without data loss**. Free automatic backups and free snapshots are included on these plans, and you should use both: snapshot before every WordPress core or plugin update, and let the scheduled backups run. Newer locations have also moved to AMD EPYC hardware with NVMe RAID-10 storage, and OS templates cover AlmaLinux, RockyLinux, CentOS, Debian, Ubuntu, CentOS Stream and Fedora, plus manual ISO installs if you want something exotic.

What you do not get is a human who fixes your website. Support covers infrastructure — your server being down, network issues, panel problems. If Apache will not start because of a typo in your .htaccess, that is a you problem, by design. Long-term users on Reddit describe exactly this arrangement, often in these exact words: they have used BandwagonHost for years, it stays up, and they knew what they signed up for. The complaints you do find trace back to the same few things — people expecting managed-style support, limited-edition plans selling out, and the CN2 GIA routes' inability to absorb DDoS attacks (capacity is limited, so attacked IPs get null-routed).

One thing worth knowing about the entry plan's 1 GB of RAM: add a 1–2 GB swap file during setup and the "but 1 GB is too small" objection mostly evaporates for a cached blog. It is the first thing to do after login anyway, before anything else.

## Getting a WordPress blog running on it

Nothing here requires heroics. This is the same stack you would deploy on any Ubuntu or Debian KVM box, and the whole process fits into an evening.

1. Pick the 20G or 40G plan, choose a datacenter near your audience (Los Angeles is the default choice for Pacific-facing blogs), and complete checkout — setup is instant, and the server details appear in KiwiVM immediately.
2. Log in over SSH, create a non-root user, enable the firewall, and add swap. Ten minutes of standard hardening.
3. Install the stack. The lazy-correct route is a WordPress stack installer such as WordOps or EasyEngine, which configures Nginx, PHP, MariaDB, and Let's Encrypt certificates in one command. Manual LEMP installation works identically if you prefer knowing every line.
4. Point your domain's DNS at the server IP, run the WordPress installer, and enable page caching before you write a single post. Caching is what makes 1 GB and 1 TB stretch to sizes that would terrify a shared-hosting account manager.
5. In KiwiVM, take a snapshot. Do it again after any major change. It is free; regrets are not.

Expect the whole thing to take one to three hours depending on how familiar you are with the command line. If reading step 2 produced a sinking feeling, that is useful information — a managed host will cost 2–8x more per year, but it removes exactly these steps.

👉 [开始搭建：选择 20G KVM 套餐](https://bit.ly/BandwagonHost)

## When BandwagonHost is the wrong answer

Honest reviews list the same scenarios, and it is better to read them now than discover them later.

If you want cPanel, one-click WordPress management, or a support chat that troubleshoots your site, buy a managed plan — this is not that product, at any price. If your workload attracts DDoS attacks and sits on a CN2 GIA route, the premium network will null-route your IP under attack rather than absorb it, which is a documented architectural limit, not a support failure. And if your audience is entirely in, say, Germany, paying Hong Kong prices buys you latency benefits you will never notice.

The fit is good when the opposite is true: you are comfortable in a terminal (or willing to become so), your blog is a real but modest workload, you want root access that shared hosting never grants, and you would rather spend $50 a year than $600. The 30-day money-back guarantee on new orders — it applies to your first purchase, not renewals, per the official refund policy — makes the first year a cheap experiment. Uptime carries a 99.9% guarantee site-wide and 99.95% on the KVM promo plans specifically.

## Getting the price even lower, without coupon-site fairy tales

Coupon aggregators currently circulate a rotating cast of BandwagonHost codes with discounts in the 5–7% recurring range, and to be fair, the provider does release codes around major sale events. But these codes expire constantly, and half the listings you will find are stale. The reliable savings do not require a code:

- **Choose annual billing.** The 40G plan is $52.99 per half-year but $99.99 per year; paying annually on the bigger plans saves 15%+ versus monthly rates. On CN2 GIA-E, annual billing saves roughly $30 a year over quarterly.
- **Watch the limited-edition restocks.** BandwagonHost periodically drops small-batch promotional plans — the community's famous "$19/year" boxes and similar — which sell out in minutes and restock irregularly. Real, but never guaranteed in stock.
- **Upgrade inside the panel.** Outgrowing the 20G plan does not mean rebuying; KiwiVM supports plan upgrades by paying the difference, keeping your data and setup intact.

👉 [浏览 BandwagonHost 全部套餐与最新库存](https://bit.ly/BandwagonHost)

## Frequently asked questions

**Is the $49.99/year plan actually real, or a bait price?**
It is the standard, openly listed price of the 20G KVM plan, billed annually, with no first-term discount trick. The reason it can exist is the self-managed model — you do the admin, they keep the price down.

**Is 1 TB of monthly transfer enough for a blog?**
For a text-and-image blog with caching, 1 TB covers on the order of half a million pageviews a month. If you exceed that, you have monetization decisions to make, not hosting emergencies.

**Do I need a CN2 GIA plan?**
Only if a significant share of your readers sits in mainland China and you care about peak-hour stability. Everyone else should buy on compute and skip the premium routing.

**Which operating system should I pick for WordPress?**
Ubuntu LTS or Debian — both are one-click templates in KiwiVM, and every WordPress deployment guide assumes one of them.

**Can I move my server to another datacenter later?**
Yes, migrations between included locations are free and performed from the panel without data loss. It is one of the more-loved features of the platform.

**What happens if I choose the wrong plan?**
You have 30 days on a new order to request a refund under the published policy, and upgrades in-panel only cost the difference. The downside of a wrong first pick is small.

## The verdict

For a blog, the search for a cheap VPS ends in one of two places. If you are willing to run your own Linux server — and for a personal or niche blog, that skill costs one wasted weekend to acquire — the 20G KVM plan at **$49.99 a year** is close to the best price-to-capability ratio available anywhere: real KVM virtualization, free backups and snapshots, free location migration, multiple datacenters, and traffic allowance that a blog will take years to outgrow. Step up to the 40G plan at $99.99 a year if you want RAM headroom or plan to consolidate a second site onto the same box.

If you are not willing to touch a terminal, no cheap unmanaged VPS will make you happy, and the right move is a managed plan at several times the price — a different purchase, not a worse one.

For everyone else, the entry plan's low price plus the 30-day refund window makes this about as low-risk as hosting decisions get.

👉 [查看 20G KVM 当前价格并开通](https://bit.ly/BandwagonHost)
