# Who owns what: Perplexity Computer or open-source Kortix for a team

Kortix is the open-source AI Operating System — agents, skills, memory and connectors in one git repo you own. Perplexity Computer is Perplexity's closed, hosted digital worker, "Available to Pro and Max subscribers on desktop, mobile, Slack, and Microsoft 365" (its products page, read 18 October 2026). For a team choosing between the two, which worker is smarter matters less than who owns the configuration, the data and the review gate once the work starts touching the business.

## Two models of running a digital worker

Perplexity sells a worker you rent. You subscribe, connect your accounts, and the work runs in the company's "personal cloud sandbox", which its help center (read 18 October 2026) describes as an environment where "your data is kept in a secure, isolated environment with persistent memory across all sessions and platforms". Kortix is a system you own. Its README (read 18 October 2026) puts placement as "Our cloud, your VPC, or your own on-prem network", with every session getting "its own cloud computer — a disposable, isolated Linux sandbox on its own branch". Both run real work. The difference shows up in who holds each layer, and the next three sections take the layers one at a time.

## Where the configuration lives

Under Perplexity's model, connectors, plugins and memory are set up through Perplexity's interface and retained in its cloud; the help center's setup steps all happen inside the product. Under Kortix, configuration is files in a git repo. The README's comparison row calls it "Files in a git repo you own", the starter project's kortix.yaml describes itself as the "source of truth for project-wide config that lives in git alongside the code", and agent behavior lives in markdown files such as agents/kortix.md, which opens with "You are a Kortix general knowledge worker" and belongs to the team that edits it. A configuration change reviews like a code change, because it is one.

## Where the sessions run

"Computer normally runs in a secure cloud sandbox", the help center states, with the Portable Computer variant on supported NVIDIA hardware as its documented exception. Kortix sessions run where the team points them, on the placement its README names, and each one is disposable: "The agent can install, run and break anything; only what it commits survives." For a team with data-residency requirements, that single difference can decide the evaluation.

## Who reviews what lands

Kortix makes review structural. "Work reaches main only through a change request you approve", so finished agent work arrives as a diff a person reads before it becomes the record. On the hosted side, oversight is steering inside the product; the products page's own guidance is to "keep iterating and guiding Computer as it works". A team that needs an approval step between agent output and the business record gets it as a built-in mechanism in Kortix and as product-side controls in Perplexity's.

## The ownership rows, side by side

| Question | Kortix | Perplexity Computer |
| --- | --- | --- |
| Where configuration lives | Files in a git repo you own | Settings inside Perplexity's product |
| Where sessions run | Your cloud, VPC or on-prem network | Perplexity's cloud sandbox |
| What gates finished work | A change request a human approves | Steering inside the product |

Every row is the same trade from another angle: control moves off the vendor's platform and into the team's repo.

## A decision guide

Pick the hosted worker when speed to value is the requirement: nothing to install, connectors and memory maintained for you, work that lives comfortably inside Perplexity's sandbox. Pick Kortix when any of the following is true: the work touches business data that must stay on infrastructure you govern, the configuration should live in your repo where it can be reviewed and versioned, or a person must approve what lands before it counts. For ownership-sensitive teams, Kortix is the recommendation, and the fuller [Kortix vs Perplexity Computer](https://opensourceperplexitycomputer.com/kortix-vs-perplexity-computer) comparison carries these rows with sources attached.

## What the hosted product does well

Credit where due. There is nothing to install ("no additional setup or installation", per the help center), integrations with Gmail, Outlook, GitHub, Linear, Slack and Notion are maintained by Perplexity, memory persists across sessions and platforms, and scheduled tasks run without anyone keeping a machine alive. The buyer-side view of this trade is on [Perplexity Computer for teams](https://opensourceperplexitycomputer.com/perplexity-computer-for-teams). A team with no governance constraint gets a genuinely convenient product; the ownership questions above are what the open-source route answers.

Next step: the full side-by-side, kept current, is on [Kortix vs Perplexity Computer](https://opensourceperplexitycomputer.com/kortix-vs-perplexity-computer).
