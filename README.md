# shared proxies: what they cost per GB, where shared IPs break, and how to pick a residential pool for scraping, geo-testing, or ad checks

Most people who type "shared proxies" into a search box aren't shopping for a brand. They're trying to solve one of two problems. Either they need a pile of IP addresses and their budget is small, or someone told them that sharing an IP is dangerous and they want to know exactly how dangerous.

Both questions come down to the same underlying detail: whether the address you're routing through is carrying someone else's traffic at the same moment you're using it. That single fact decides what you can realistically do with the proxy — more than the price does.

## What "shared proxies" actually covers

The term gets used for two different things, and they behave nothing alike.

**A static shared IP list.** You get handed a set of IP addresses, usually datacenter ranges, and you pick one to use until you feel like switching to another. Providers in this segment typically cap the number of users per address at around five, which is what separates a paid shared proxy from a free public one. There's no automatic rotation — you manage that yourself. Payment is normally per IP.

**A rotating shared pool.** You connect to one gateway address, and the provider assigns you an exit IP from a large pool. Rotation can be per request or timed, and in sticky mode you keep the same IP for a window you define. You don't own any individual address, which is the entire point: you get variety without paying for exclusivity.

Residential proxies almost always fall into the second category. That's the model where "shared" is baked into the architecture rather than being a budget compromise — the pool exists precisely because many customers rotate through it.

If you want the short version of how the options stack up:

| Type | Who else is on the IP | Typical pricing | Where it holds up |
| --- | --- | --- | --- |
| Free public proxy | Anyone, unlimited | $0 | Feature testing, nothing you care about getting blocked |
| Shared static list | Up to a handful of users | Cheapest paid tier, often per IP | Geo-unblocking, low-stakes browsing |
| Rotating shared pool | Time-shared across a pool | Usually per GB | Scraping, price checks, ad verification, SERP tracking |
| Dedicated / private | Nobody | Roughly an order of magnitude more per unit | Account-sensitive work, payment flows, high success-rate targets |

The gap between the middle two rows and the last one isn't about speed. It's about who else gets blamed when a target site decides an IP has misbehaved.

## The cost math, and why it's not as simple as "$0.68 per GB"

Published 2026 roundups put budget residential bandwidth somewhere around $0.70–$2 per GB at standard volumes, with the cheapest tier reserved for large commitments. Dedicated IPs cost far more for the same amount of work because you're paying for exclusivity rather than bandwidth.

That spread explains most buying decisions. If your job is thousands of requests against moderately protected sites, a rotating shared pool at sub-$1/GB is the rational choice. If your job is keeping a dozen accounts logged in for months, cheap shared bandwidth is the wrong tool regardless of how little it costs.

One thing worth internalizing: with a shared pool, the per-GB rate is the only number the vendor controls. How many of those gigabytes arrive successfully is not part of the sticker price.

## Where shared IPs actually break

Four failure modes show up again and again, and they're all structural.

**Bad neighbours.** Someone else's aggressive scraping on an address you happen to be using gets that address banned, and you inherit the ban. Industry guides usually put the added block rate from neighbour abuse at a few percentage points — small on paper, painful when it hits your target.

**Throughput swings.** Shared bandwidth means shared contention. One provider's own documentation puts speed variation during peak hours at 15–30% on shared pools versus under 5% on dedicated ones. You won't notice on a geo-check; you will notice on a long scrape.

**No visible history.** In most shared pools you can't inspect an IP's block history before you use it. You find out by getting a wall.

**No control over load or rotation policy.** The vendor decides the rotation logic and how many users sit on an address. You configure within those limits.

Which tasks survive that list: geo-restricted browsing, low-volume price monitoring, ad verification across many markets, small-scale rank checks, and light scraping against targets that aren't heavily defended. Which tasks don't: payment flows, sensitive account management, and high-volume work against protected sites, where the block rate climbs enough to wipe out the savings.

If you want a shared residential pool and you'd rather not guess at the failure rates, [👉 compare the current 9Proxy residential pool specs and pricing](https://bit.ly/9-Proxy) before you start running tests.

## What 9Proxy sells, and which part of it is "shared"

9Proxy is a residential proxy provider, not a datacenter shared-IP shop. Its live catalogue is residential-only, which matters if what you actually wanted was a cheap static datacenter list — that's a different market and 9Proxy doesn't play in it.

The platform runs two models:

**Residential by IP.** You buy a fixed number of residential IPs and use them with no bandwidth cap. Unused IPs don't expire. Each IP stays active for a few hours up to roughly 24 hours, and one IP is consumed per forward, so this is closer to a session-based dedicated IP than to a multi-tenant shared address. There's no natural rotation; automatic rotation is available through the Auto Rotation Proxy feature on selected ports. Authentication runs through the desktop app with local port forwarding.

**Residential by GB.** You buy traffic and generate unlimited endpoints from the pool. Sessions can be sticky or rotating, with per-request or timed switching. This is the genuinely shared model: you're drawing from a 20M+ residential IP pool spanning 90+ countries, targeting down to country, state, city, ZIP code, and ISP, with no individual IP reserved for you. It works straight from the dashboard — no app required — and authenticates with username/password or an IP whitelist.

That second model is what most people searching "shared proxies" actually want. The first is for the cases where sharing is the problem.

## Every current 9Proxy package

Note that 9Proxy adjusted pricing on 1 June 2026 for its IP-based and bundle products, while GB-based pricing stayed where it was. The table below reflects the post-adjustment numbers. Because the system is balance-based, IPs purchased never expire; GB traffic carries 180-day validity unless you're on an Enterprise package, where it doesn't expire at all.

| Package | What you get | Price | Validity | Buy |
| --- | --- | --- | --- | --- |
| 100 IPs | $0.24 per IP, unlimited bandwidth | $24 | IPs never expire | [ Buy 100 IPs](https://bit.ly/9-Proxy) |
| 500 IPs | $0.144 per IP | $72 | IPs never expire | [ Buy 500 IPs](https://bit.ly/9-Proxy) |
| 1,000 + 500 bonus IPs | $0.084 per IP, 1,500 total | $126 | IPs never expire | [ Buy the 1,500-IP package](https://bit.ly/9-Proxy) |
| 2,500 IPs | $0.084 per IP | $210 | IPs never expire | [ Buy 2,500 IPs](https://bit.ly/9-Proxy) |
| 5,000 IPs | $0.072 per IP | $360 | IPs never expire | [ Buy 5,000 IPs](https://bit.ly/9-Proxy) |
| 15,000 IPs | $0.048 per IP | $720 | IPs never expire | [ Buy 15,000 IPs](https://bit.ly/9-Proxy) |
| 25,000 IPs | $0.035 per IP | $863 | IPs never expire | [ Buy 25,000 IPs](https://bit.ly/9-Proxy) |
| 50,000 IPs | $0.029 per IP | $1,438 | IPs never expire | [ Buy 50,000 IPs](https://bit.ly/9-Proxy) |
| Business: 100,000 IPs | $0.023 per IP | $2,300 | IPs never expire | [ Buy the 100k IP business package](https://bit.ly/9-Proxy) |
| Business: 200,000 IPs | $0.021 per IP | $4,140 | IPs never expire | [ Buy the 200k IP business package](https://bit.ly/9-Proxy) |
| Business: 500,000 IPs | $0.018 per IP | $8,625 | IPs never expire | [ Buy the 500k IP business package](https://bit.ly/9-Proxy) |
| 5 GB | $3.00 per GB | $15 | 180 days | [ Buy 5 GB](https://bit.ly/9-Proxy) |
| 50 GB + 5 GB bonus | $2.10 per GB, 55 GB total | $105 | 180 days | [ Buy the 55 GB package](https://bit.ly/9-Proxy) |
| 100 GB | $1.50 per GB | $150 | 180 days | [ Buy 100 GB](https://bit.ly/9-Proxy) |
| 200 GB | $1.00 per GB | $200 | 180 days | [ Buy 200 GB](https://bit.ly/9-Proxy) |
| 1,000 GB | $0.80 per GB | $800 | 180 days | [ Buy 1,000 GB](https://bit.ly/9-Proxy) |
| 2,000 GB | $0.75 per GB | $1,500 | 180 days | [ Buy 2,000 GB](https://bit.ly/9-Proxy) |
| Enterprise 3,000 GB | $0.72 per GB | $2,160 | Unlimited | [ Buy the 3,000 GB enterprise package](https://bit.ly/9-Proxy) |
| Enterprise 6,000 GB | $0.70 per GB | $4,200 | Unlimited | [ Buy the 6,000 GB enterprise package](https://bit.ly/9-Proxy) |
| Enterprise 10,000 GB | $0.68 per GB | $6,800 | Unlimited | [ Buy the 10,000 GB enterprise package](https://bit.ly/9-Proxy) |
| Starter Bundle | 100 IPs + 5 GB | $30 | Traffic 180 days, IPs never expire | [ Buy the Starter bundle](https://bit.ly/9-Proxy) |
| Popular Bundle | 1,500 IPs + 50 GB | $180 | Traffic 180 days, IPs never expire | [ Buy the Popular bundle](https://bit.ly/9-Proxy) |
| Pro Bundle | 5,000 IPs + 500 GB | $720 | Traffic 180 days, IPs never expire | [ Buy the Pro bundle](https://bit.ly/9-Proxy) |

Prices shift, and the vendor has already changed them once in 2026, so treat this table as a snapshot of the current listing rather than a permanent contract. Independent 2026 comparisons generally place 9Proxy in the budget residential band, around $1–2/GB at typical volumes, which lines up with the mid-tier GB rows above.

A couple of honest observations about this lineup. The IP-based packages are cheap per unit, but an IP that lives a few hours to about 24 hours is not a long-lived static proxy, and 9Proxy says so plainly. If you need an address that stays put for months, this isn't it. And if you're reselling or running a team, the Enterprise tier's team mode (one owner plus up to five members, with shared bandwidth that doesn't expire inside the team) is where the pricing starts to make sense at volume.

## Which package fits which job

**Occasional geo-checks and small verification runs.** The 5 GB package at $15. You can burn through a surprising number of checks on five gigabytes when each request is a single page.

**Price monitoring, SERP tracking, routine scraping.** Anything in the 100–1,000 GB range. At $1.50/GB down to $0.80/GB, the per-request cost is low enough that rotating freely stops being a budget decision.

**Stable sessions for a few hundred targets.** The 100-IP or 500-IP packages. Paying per IP with unlimited bandwidth is better than paying per GB when your requests are heavy but your IP count doesn't need to be large.

**Agencies juggling mixed client work.** The bundles. Paying $30 for 100 IPs plus 5 GB is cheaper than buying those two things separately, and the traffic carries 180-day validity so an uneven month doesn't waste it.

**Always-on infrastructure.** The 3,000 GB Enterprise tier and up, mainly for the unlimited validity and team features rather than the modest per-GB saving.

If you'd rather test than calculate, [👉 start with the smallest 9Proxy GB package and measure success rate on your own targets](https://bit.ly/9-Proxy) — five gigabytes is enough to find out whether a shared residential pool handles the sites you care about.

## Testing a shared pool without burning money

Trials exist but availability is limited — the vendor says trial provisioning depends on stock and you need to say whether you want an IP-based or GB-based trial. Don't plan a project around getting one.

The reliable approach is to buy the smallest package that lets you measure something real, then check four things:

1. **Success rate on your actual targets.** A generic 99% claim means nothing if your specific site blocks the pool. Use the sites you'll be scraping, not a test page.
2. **Latency distribution.** Run a few hundred requests and look at the tail, not the average. Shared pools are defined by their bad minutes.
3. **Session stability in sticky mode.** If your workflow needs the same IP across a login and follow-up requests, verify the session actually holds for the window you configure.
4. **Block rate after rotation.** Rotate aggressively for an hour and see whether bans cluster on specific addresses. That tells you how clean the pool is in regions you need.

Signing up through an invite code path is how the referral discount gets applied, and 9Proxy also advertises a 5% discount or 5% traffic bonus on selected payment methods — worth a look before completing checkout, since it applies to the order rather than after it.

## Setup details people miss

The IP-based model requires the 9Proxy desktop app with local port forwarding, which is fine on a machine you control and awkward on a server you don't. The GB model runs entirely from the dashboard, so it's the one that drops into cloud workflows and CI jobs without extra plumbing. Both support HTTP/HTTPS and SOCKS5.

Authentication differs too. GB-based sessions use username/password or an IP whitelist; IP-based sessions lean on the app with optional proxy authentication on top.

Sharing is supported but structured. 9Proxy allows account sharing with multiple people and provides share codes and sub-accounts, while the Enterprise tier adds team mode with per-member traffic controls and activity logs. If "shared" for you means sharing with colleagues rather than sharing with strangers, that's the relevant feature.

Payments accepted include credit cards, bank cards, cryptocurrency (USDT, BTC, ETH, LTC, DOGE and others), Alipay, Apple Pay, and Google Pay.

## When shared proxies are the wrong tool

Skip them for anything where a ban costs more than the bandwidth saved: payment systems, primary social or marketplace accounts, advertising campaigns that need stable delivery, and scraping runs where a few extra percentage points of block rate translates into hours of engineering time.

The most common mistake isn't choosing a shared proxy. It's choosing a free one. Free public proxies are open to everyone, get overloaded, disappear without notice, and in the worst case route your traffic through someone who is reading it. A paid shared pool at under a dollar a gigabyte exists precisely to remove that class of problem.

## Quick answers to the usual questions

**Is a shared proxy safe for scraping?** For light to moderate volume against less protected targets, yes. High-volume runs or frequent login attempts on defended sites trigger detection faster because the IP isn't yours alone.

**What's the difference between shared and rotating?** Rotation is a feature, sharing is a funding model. A shared pool can rotate; a dedicated IP usually can't. Static shared lists give you several IPs and leave the switching to you.

**Do shared IPs slow down my connection?** Sometimes. Expect noticeable variation at peak hours, and treat that as normal rather than a fault.

**Can I get a residential IP that nobody else uses?** Yes, but you'll pay for exclusivity. 9Proxy's IP-based model is the closest thing on its list: a session-scoped address with unlimited bandwidth, which is a different trade-off from a permanent private IP.

**What happens to unused balance?** On 9Proxy, purchased IPs don't expire, GB traffic stays valid for 180 days on standard packages, and Enterprise bandwidth has no expiry at all.

The short version: shared proxies are a reasonable engineering choice for a specific band of work — cheap IP diversity on targets that aren't paranoid. The mistake is treating the cheapest tier as a universal answer. Pick the pool, measure the success rate on your own targets, and let that number, not the price list, decide whether you scale up.
