# What Perplexity Computer is, and where the open-source alternative differs

Kortix is the open-source AI Operating System — agents, skills, memory and connectors in one git repo you own. Perplexity Computer is the closed, hosted product it gets compared with, and it deserves the same plain definition. Perplexity's own pages supply one; the interesting part is where the software runs.

Perplexity Computer is a hosted digital worker. The company's products page (read 18 October 2026) introduces it as "a general-purpose digital worker that operates the same interfaces you do", one that "creates and executes entire workflows, capable of running for hours or even months". You hand it a task in plain language, and the page says "Computer deploys subagents to handle the rest". Access is by subscription: the worker is "Available to Pro and Max subscribers on desktop, mobile, Slack, and Microsoft 365", and Perplexity's help center adds that there is "no additional setup or installation" beyond an active subscription.

## What it does, according to Perplexity

The capability list comes from two Perplexity pages, both read on 18 October 2026. The products page lists recurring background tasks that Computer "executes autonomously and persistently over time", parallel research with browser automation, and connectors: "Connect Gmail, Slack, Notion, Calendar, and hundreds of other tools." The help center's article on what Computer is adds "authenticated integrations with Gmail, Outlook, GitHub, Linear, Slack, Notion, and more", "persistent memory that retains context across sessions", and scheduling and automation "for recurring tasks". In short: you prompt, it plans and works through your connected accounts, and it keeps operating on a schedule while you are away. A longer walkthrough of [what a Perplexity Computer is](https://opensourceperplexitycomputer.com/what-is-a-perplexity-computer), quote by quote, sits on the comparison site.

## What "operates the same interfaces you do" means for a team

The phrase is accurate, and the location matters as much as the action. The interfaces get operated from inside Perplexity's cloud. The help center describes the working environment as a "personal cloud sandbox" where "your data is kept in a secure, isolated environment with persistent memory across all sessions and platforms". Connector credentials, accumulated memory and task history sit in Perplexity's product, on Perplexity's infrastructure, under Perplexity's controls. A team can use all of it. What it cannot do is read the code that drives the worker, host that worker on its own terms, or move the memory into a system it owns.

Perplexity documents one partial exception. "On supported NVIDIA hardware, Portable Computer runs the model, orchestrator, scheduler, and sandbox on your own device instead", the help center says, and local work "does not consume credits"; steps that need the web or a frontier model are "escalated to the cloud only with your permission". Portable Computer is still Perplexity's closed application, now running on your own hardware. It changes where the bytes sit. It does not hand a team source code to audit or a system to own. Whether [Perplexity Computer is open source](https://opensourceperplexitycomputer.com/is-perplexity-computer-open-source) has a short answer, and that page works through it properly.

## Where the open-source alternative differs

Kortix answers those limits structurally. Its README (read 18 October 2026) states the source position as "Open source — read it, fork it, audit it", and placement as "Our cloud, your VPC, or your own on-prem network". Every session gets "its own cloud computer — a disposable, isolated Linux sandbox on its own branch", and work reaches main only through "a change request you approve". Configuration lives in the repo: the starter project's kortix.yaml describes itself as the "source of truth for project-wide config that lives in git alongside the code", and each agent's behavior is a markdown file the team edits and versions like any other code. When the runtime, the memory and the review step are things the team holds, Perplexity's own description reads differently: same interfaces, different owner.

## Who should still consider it

The hosted product earns its audience. Nothing to install, nothing to patch, connectors and memory maintained by the vendor, and a worker that already lives inside Slack and Microsoft 365. A team with no requirement to audit or self-host anything gets a genuinely convenient product for its spend. Kortix stays the recommendation where ownership is the requirement, and that is the case for the teams this repo serves.

Next step: the full definition, quote by quote with dates, is on [what a Perplexity Computer is](https://opensourceperplexitycomputer.com/what-is-a-perplexity-computer).
