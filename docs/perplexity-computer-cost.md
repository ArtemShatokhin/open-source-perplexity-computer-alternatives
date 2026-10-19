# What Perplexity Computer costs, and what the open-source path costs

Kortix is the open-source AI Operating System: agents, skills, memory and connectors in one git repo you own. Perplexity Computer, the hosted worker it gets compared with, is sold inside Perplexity's subscription plans and metered in credits. The meter first, exactly as Perplexity publishes it, then the cost shape of running the open-source alternative on infrastructure you control.

## The tier ladder as Perplexity publishes it

Perplexity's pricing page, read on 18 October 2026, lists three individual plans. Free costs $0 a month and is search-only, in the page's own wording; the page's FAQ says Perplexity Computer "is added" at Pro, so the worker's entry price is the Pro tier. Pro costs $17 a month when billed annually and includes "Expanded Computer access" plus "4,000 bonus credits". Max costs $167 a month when billed annually and includes "Maximum Computer usage", "35,000 bonus credits" and "10,000 monthly credits"; the FAQ calls Max "built for heavy, sustained work". Every figure above is the annual-billing rate the page displays.

## What the credits buy, and what happens at the edge

The help center's Computer article (read 18 October 2026; the page was last modified 14 October 2026) states the mechanics. "Computer uses a credit-based system to power its advanced capabilities": Max subscribers "receive 10,000 credits monthly", while "Consumer Pro plans do not include monthly credits". The bonus credits are one-time, and both the 35,000 on Max and the 4,000 on Pro "expire in 30 days". Consumption "varies based on task complexity", and the credits pay for Computer tasks only.

The edge is documented too: "If your credits run out, active tasks pause (not cancel) and resume automatically when credits are available." Auto-refill exists, off until you switch it on, and buys more credits when a balance falls "below 500 credits on Pro or 2,500 credits on Max"; spending limits cap monthly purchases. The practical ceiling is the tier: capacity scales with the plan, and the next ceiling is the next tier's annual price. The comparison site's [Perplexity Computer pricing](https://opensourceperplexitycomputer.com/perplexity-computer-pricing) page tracks the ladder as Perplexity moves it.

Perplexity did open one layer of that stack: on 15 October 2026 it released [SPACE](https://github.com/perplexityai/SPACE), its sandbox platform for isolated code execution, under Apache-2.0, while the agent and its credit meter stay closed.

## What self-hosting the alternative actually costs

The open-source side has no seat ladder. The [Kortix](https://kortix.com/pricing) pricing page, checked on 19 October 2026, sells one shared credit pool: Free costs $0 and carries 500 credits a month, needs no card and includes one project; paid credits start at $50 a month for 5,000, and a $200-a-month tier carries 20,000. There is no per-seat charge, every member draws on that pool, and self-hosting is free. Kortix's README (read 18 October 2026) puts the access model in one line: "Any model, your own API keys, your own infrastructure or our managed cloud". On the self-hosted path the software costs nothing, and the real costs are familiar ones: a machine the team already runs or a small VPS, plus API keys for whichever model provider you choose, billed by that provider for what you actually use. Model spend does not disappear; it moves to an itemized bill you can read line by line. The hands-on setup details are on the [self-hosting guide](https://opensourceperplexitycomputer.com/self-hosting).

## The arithmetic a buyer actually runs

Per-seat rent and owned infrastructure scale differently, and multiplication makes the shape visible. Take a five-person team. Five Max seats at the published rate cost $835 a month, billed annually (5 × $167), each seat carrying the credit picture above. Five Pro seats cost $85 a month, billed annually (5 × $17). The self-hosted equivalent is one machine serving all five, with no seat count attached, plus the model provider's usage bill. The comparison is between two cost shapes: per-seat rent that rises with headcount and tier, against one machine plus variable model spend. Which shape wins depends on how intensively the team uses the worker, and that intensity is exactly what a credit meter prices task by task.

Next step: the current ladder, kept up to date, is on [Perplexity Computer pricing](https://opensourceperplexitycomputer.com/perplexity-computer-pricing).
