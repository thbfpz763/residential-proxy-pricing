# residential proxy services: cost per successful request, targeting add-ons, and the $5 test that decides it

Three kinds of people search for residential proxy services, and they all end up staring at the same pricing table.

The first is someone whose scraper worked fine last month and now returns 403s on half its requests. The second needs to see a website the way a logged-in user in Frankfurt or São Paulo sees it, and a VPN with one shared exit IP stopped cutting it. The third is holding an invoice and trying to work out why "from $1 per GB" turned into $340.

The table on most vendor pages won't answer the question all three actually have: what does one *successful* request cost? A pool at $0.50/GB that gets blocked 40% of the time is more expensive than a clean pool at $1/GB. This article walks through the pricing units that don't compare to each other, the targeting surcharges that quietly double your effective rate, and a cheap way to test any pool before you commit real budget. DataImpulse, a pay-as-you-go provider with residential traffic from $1/GB, is the worked example throughout.

## What you're buying when you rent residential IPs

A residential proxy routes your request through an IP address assigned by a consumer ISP to an actual household connection. To the website on the other end, the traffic looks like a person on a home broadband line rather than a server in a datacenter rack. That difference is the entire product.

The four common types in this market:

- **Residential**: real ISP-assigned consumer IPs, rotating by request or held for a session. The default for defended targets (marketplaces, SERPs, social platforms).
- **Datacenter**: hosted server IPs. Fast and cheap, and increasingly detected. Fine for unprotected targets and high-volume jobs where nothing is fighting back.
- **Mobile**: 4G/5G carrier IPs. The scarcest and most trusted, and priced accordingly.
- **ISP / static residential**: datacenter-hosted but ISP-registered IPs, rented per IP per month. Used for account management where you need one stable address for weeks.

Where the IPs come from matters more than the pool size on the banner. Several large proxy networks have been taken down or sued over how they recruited devices, which turned sourcing from a compliance footnote into a buying criterion. A provider should be able to name the opt-in flow, confirm that participants are compensated, and hand over a data processing agreement. Vague answers about where the bandwidth comes from, or a price far below the rest of the market with no explanation, are the two signals worth walking away from.

DataImpulse builds its pool through its own disclosed SDK and its TraffMonetizer bandwidth-sharing app, and publishes sourcing details alongside a DPA request path. Whether you trust that is your call, but it's the kind of answer the question deserves.

## The three billing units, and why they aren't comparable

Providers price residential traffic in three ways, and the units measure different things:

| Billing unit | Typical products | What it hides |
| --- | --- | --- |
| Per GB of transfer | Residential, mobile, datacenter | Expiring traffic, low success rates, per-request overhead |
| Per IP per month | ISP/static residential, dedicated datacenter | Bandwidth caps on each IP |
| Per 1,000 requests | Managed scraper and SERP APIs | The engineering work you no longer pay for |

$1/GB and $2 per 1,000 requests cannot be ranked on the same axis without knowing your average page size and your success rate. Convert both to cost per successful request and the comparison gets honest. A 500 KB page at $1/GB works out to roughly $0.0005 per request, or about $0.50 per thousand. A managed API at $2 per 1,000 is four times that, but it also handles rotation, headless rendering and anti-bot for you, which is the trade you're making.

The per-GB model wins for scraping you run yourself at volume. The per-IP model wins when you need four or five stable addresses pushing a lot of data each. Managed APIs win at low volume or when nobody on the team wants to write retry logic.

One more thing buried in the per-GB model: whether the traffic expires. A monthly allotment that resets to zero on the 1st is a subscription you're paying for even in months you don't use it. Pay-as-you-go balance that rolls over changes the math for anyone with uneven workload.

## What a normal price looks like

The spread in this market is wide and it's real. Decodo publishes residential monthly plans starting at $11.25 for 3 GB, which is $3.75/GB, scaling down to $2/GB at the 1 TB tier, with $4/GB for pay-as-you-go. Bright Data describes a 400M+ residential IP pool across 195+ countries on an opt-in compensation model. Neither number is a marketing trick; bigger, freshly vetted, ethically sourced pools cost more to run.

Against that backdrop, a flat $1/GB pay-as-you-go rate with no monthly minimum sits at the low end of the range, and it's why DataImpulse keeps showing up in price-per-GB comparisons. What it doesn't buy you is a managed scraping API, static ISP proxies, or access to banking and government sites. The full plan list below makes the trade-offs visible.

## Every DataImpulse plan on the price list

Everything here is pay-as-you-go. There's no subscription, no monthly minimum beyond the entry purchase, and country-level targeting is included in the per-GB rate. The tiers are volume price breaks, not locked bundles, and unused balance doesn't expire.

| Proxy type | Package | Price | Effective rate | Best for | Buy |
| --- | --- | --- | --- | --- | --- |
| Residential | 5 GB (entry) | $5 | $1.00/GB | Testing a pool on your own targets | Start with the $5 residential pack |
| Residential | 50 GB | $50 | $1.00/GB | Ongoing scraping on defended sites | Get 50 GB of residential traffic |
| Residential | 100 GB | $100 | $1.00/GB | Mid-volume production jobs | Load 100 GB |
| Residential | 1 TB | $800 | $0.80/GB | High-volume pipelines | Buy the 1 TB residential tier |
| Residential | 5 TB | Custom | $0.70/GB | Large-scale continuous collection | Request 5 TB residential pricing |
| Datacenter | 10 GB | $5 | $0.50/GB | Fast, low-cost, unprotected targets | Get 10 GB of datacenter traffic |
| Datacenter | 100 GB | $50 | $0.50/GB | Bulk crawling without anti-bot | Load 100 GB datacenter |
| Datacenter | 1 TB | $450 | $0.45/GB | Sustained high-speed runs | Buy the 1 TB datacenter tier |
| Datacenter | 5 TB+ | Custom | Volume rate | Enterprise-scale throughput | Ask about datacenter volume pricing |
| Mobile | 2.5 GB | $5 | $2.00/GB | Hardest targets, app and mobile-web data | Get 2.5 GB of mobile traffic |
| Mobile | 25 GB | $50 | $2.00/GB | Account work needing carrier IPs | Load 25 GB mobile |
| Mobile | 1 TB | $1,600 | $1.60/GB | Large mobile-data workloads | Buy the 1 TB mobile tier |
| Mobile | 5 TB+ | Custom | Volume rate | Carrier-scale operations | Request mobile volume pricing |
| Premium residential | 1 GB | $5 | $5.00/GB | Lowest latency, all targeting included | Try 1 GB premium residential |
| Premium residential | 10 GB | $50 | $5.00/GB | Latency-sensitive production work | Load 10 GB premium residential |
| Premium residential | 5 TB+ | Custom | Volume rate | Enterprise residential at scale | Ask about premium volume pricing |

Two things in that table are worth pointing out.

First, premium residential includes all targeting options with no surcharge and adds a dedicated account manager, which is the closest thing to an enterprise tier here. Second, the effective rate only drops below $1/GB at the 1 TB and 5 TB residential tiers, so if you're moving 30 GB a month, the flat $1/GB is what you pay. That's the honest reading.

## Where the per-GB price stops being the whole bill

The rate is the start of the calculation, not the end.

**Targeting add-ons.** Country targeting is free on every plan. City, ZIP and ASN filtering are paid extras. A third-party breakdown of DataImpulse's pricing updated in September 2026 states that on the standard residential tier, traffic routed through advanced target filters bills at double the base per-GB rate, and advises confirming the surcharge with support before you plan a budget around it. That advice is worth taking regardless of which provider you use, because city-level targeting is exactly the feature most people underestimate when they estimate cost.

**Success rate.** DataImpulse publishes a 99.51% success rate. Treat published numbers as directionally useful and your own logs as authoritative. A pool that returns 60% usable responses at $0.50/GB is more expensive per usable record than a clean pool at $1/GB, and no marketing page will do that arithmetic for you.

**Traffic expiry.** Nothing here expires. That's the single most underrated line in the whole plan list.

**Refunds.** New users get a 7-day refund window on the entry plan, with crypto payments excluded. Reasonable, but not a substitute for testing on your own targets in the first place.

## Getting traffic flowing without a support ticket

Setup is deliberately plain. The gateway is `gw.dataimpulse.com`, with port 823 for HTTP/HTTPS and port 824 for SOCKS5. Authentication is username and password, or IP whitelisting if you'd rather not pass credentials through a tool.

Targeting and session control live in the username string, which is a neat trick once you've seen it and baffling until you have. A working example looks like this:


YOUR_LOGIN__cr.us;city.newyork;sessid.profile01:YOUR_PASSWORD@gw.dataimpulse.com:823


`__cr.us` pins the country, `;city.newyork` narrows it to a city, and `sessid.profile01` holds one IP for that thread instead of rotating on every request. Give each account or browser profile its own sessid. Reusing one sessid across two profiles puts both on the same IP, which is the fastest way to get both of them flagged.

On session length, a TechRadar review of the service notes that sticky sessions are port-based and rotation intervals run from 1 to 120 minutes, while rotating proxies change IP with each new request. That's the practical range to design around: short sessions for scraping, long ones for logins and account work.

There are copy-paste snippets for Python, Node.js, PHP, C#, Go, Ruby and cURL, and setup guides for Scrapy, Puppeteer, Selenium, Playwright, AdsPower, Multilogin, Octoparse and Zapier. The same review points out that DataImpulse offers raw proxy connections only, with no managed scraping API and no built-in CAPTCHA solving, so retries and parsing stay on your side of the fence. If you want somebody else to own that layer, you're shopping in the wrong category.

## When a raw residential pool is the wrong tool

DataImpulse's own documentation is unusually direct about the mismatch, which is worth repeating: it isn't the right pick if you need static ISP proxies, a fully managed scraping API, or access to banking and government sites. It sells rotating residential, mobile and datacenter traffic for collecting public data.

What that means in practice:

- You need one IP address that never changes for six months → you want ISP/static residential, not a rotating pool.
- You want to send a URL and get parsed JSON back → you want a managed scraper API.
- You need 15 billion pages a month → talk to enterprise providers about custom infrastructure and SLAs.

For everything else, the per-GB model is the cheaper shape.

## The $5 afternoon test

Here's the version of "due diligence" that costs almost nothing and tells you more than any review.

Buy the entry pack. 👉 Pick up the 5 GB starting balance for $5 — non-expiring, no subscription, and enough for roughly 10,000 page loads at an average 500 KB per page.

Then:

1. Pick three URLs that represent your hardest targets, not your easiest ones. Product pages behind Cloudflare, a SERP, a regional storefront that geo-blocks you.
2. Run 500 to 1,000 requests through the rotating gateway at country level, and log the HTTP status and bytes returned for each one.
3. Re-run a smaller batch with sticky sessions and city targeting if your use case needs them, and note how the volume burns faster.
4. Divide your spend by the number of responses that were actually usable.

That last number is your real cost per successful request, and it's the only figure worth comparing across providers. At $1/GB, 1,000 half-megabyte pages cost about 50 cents. Even if you rerun the test three times with different targeting settings, you're out a couple of dollars, and you'll know whether a $3.75/GB alternative is genuinely better for your target list or just more expensive.

## Questions people ask before buying

### How much do residential proxy services cost per GB?

It varies by pool quality and sourcing. Pay-as-you-go entry rates sit around $1/GB, mainstream monthly plans land closer to $3 to $4/GB, and enterprise-oriented providers top $5/GB. Judge by cost per successful request rather than the headline figure, since expiring traffic, targeting surcharges and low success rates all push the real number up.

### Does purchased traffic expire?

On DataImpulse, no. Balances roll over and stay usable until you consume them. Many competitors expire unused bandwidth at the end of a billing cycle, which is the main reason a lower sticker price can end up costing more per usable gigabyte.

### Is there a free trial?

There's no free plan. The entry point is the $5 / 5 GB residential pack, and new users have a 7-day refund window on it, excluding crypto payments. Compared with providers that gate everything behind a subscription, five dollars is a cheap way to measure results on your own traffic.

### Residential, mobile, datacenter or premium residential?

Datacenter for cheap, fast, unprotected targets. Residential for defended sites and anything resembling a real user session. Mobile when carrier IPs are the only thing that gets through, and premium residential when latency and full targeting matter more than the per-GB rate.

### What payment methods are accepted?

Credit and debit cards, PayPal, wire transfer, cryptocurrency, Alipay, Apple Pay and Google Pay.

## The short version

The number on a residential proxy pricing page is a starting point, not a bill. What decides the bill is how much of your traffic comes back usable, how much extra the targeting you actually need costs, and whether the balance survives past the end of the month.

If your workload is uneven, your volume is under a terabyte, and your targets fight back, a flat $1/GB pay-as-you-go model with non-expiring traffic is hard to argue with. 👉 Check the current residential proxy plans and the $5 entry pack, run the afternoon test against your own targets, and let your own logs tell you whether the rate is worth it.
