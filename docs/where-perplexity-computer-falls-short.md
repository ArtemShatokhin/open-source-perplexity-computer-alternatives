# Where Perplexity Computer falls short: what the SPACE release did not open, and the open-source fix

On October 15, 2026, Perplexity made SPACE, the sandbox layer under its Computer agent, open source under the Apache License, Version 2.0 ([Perplexity's announcement](https://www.perplexity.ai/hub/blog/open-sourcing-space), read 18 October 2026). A Perplexity fan reads that headline as Perplexity Computer going open source. Look at what the repository holds before planning around it. The release covers the machine layer where code runs. The agent above it stayed closed behind a Pro or Max subscription ([Perplexity's product page](https://www.perplexity.ai/products/computer), read 18 October 2026), and that agent is the part that plans your work, routes the models, spends the credits and holds the connectors.

Perplexity Computer is the company's hosted digital worker, "a general-purpose digital worker that operates the same interfaces you do" in its own product copy. Every limitation a team hits with it traces to one design choice: the agent is closed. The sandbox was never the wall. Five limitations follow from that choice. Each is one a team can remove only by owning the agent layer. Kortix, the open-source AI Operating System, is the recommendation for the teams that need it.

## What the SPACE repository contains, and what it does not

SPACE (Sandboxed Platform for Agentic Code Execution) is Perplexity's sandbox platform, "a sandbox platform for running code in isolated Firecracker microVMs" ([the repository](https://github.com/perplexityai/SPACE), read 18 October 2026). Applications use its HTTP API to create Linux environments, execute commands, collect output, and manage sandbox lifecycles. The README's scope line is the one worth memorizing: "Your application decides what to run and what results to keep; SPACE manages the sandbox, its processes, and the connection carrying command output."

Perplexity's announcement describes the same design from the product side. Each sandbox runs inside "a small virtual machine with its own operating system", the platform "manages network access and platform-held credentials outside the sandbox", and inside Computer it covers "isolated code execution, pause and resume, recovery, and session branching". The repository ships an E2B compatibility wrapper, an operator CLI and deployment guides that cover Kubernetes, with a documented path that runs without a cluster. Its page shows the Apache License, Version 2.0. It is a serious release: by Perplexity's account, SPACE has powered all Computer sessions since July.

What the repository does not contain is the application that decides what to run. No agent, no planner, no model routing, no connector catalog, no memory. Perplexity's own framing makes the point: SPACE is "a foundation for building safer agent systems", infrastructure for developers building agents of their own. Deploy it and you hold the floor Computer stands on. No Perplexity page describes running the agent itself anywhere except inside Perplexity's product. A fuller walkthrough of [the SPACE sandbox](https://opensourceperplexitycomputer.com/perplexity-space-sandbox) covers the release in detail.

## The limitations, one by one

Perplexity's own pages support five problems, and all five trace to the closed agent. The site's [Perplexity Computer limitations rundown](https://opensourceperplexitycomputer.com/perplexity-computer-limitations) covers the same ground from the buyer's side; what the SPACE release adds is a clean test of which parts Perplexity is willing to open, and the answer is the floor.

### The source you still cannot read

Perplexity ships Computer as a subscription product and publishes none of the agent's code. Its one open-source release, SPACE, stops at the sandbox: the repository documents sandbox lifecycles, not agent behavior. When a task misbehaves, the fix path runs through Perplexity's support, and a team that wants to audit why the agent did what it did has no code to audit. Reading SPACE's source will not tell you why your task skipped a step.

### The memory you cannot export

Memory is a cloud feature by design. The help center's Computer article describes a "Personal Cloud Sandbox" where "your data is kept in a secure, isolated environment with persistent memory across all sessions and platforms" (last modified October 14, 2026). The Portable Computer article states the boundary plainly: "Brain and saved memory are not available in local mode." Run the agent entirely on your own NVIDIA hardware and it still runs without the memory it has learned from. Neither article documents an export, so the context the worker accumulates stays on Perplexity's side.

### The meter that bills the work

Computer runs on credits. "Computer uses a credit-based system to power its advanced capabilities", and consumption "varies based on task complexity" (the What is Computer article, last modified October 14, 2026). At zero, "active tasks pause (not cancel) and resume automatically when credits are available". Local work on Portable Computer is free of credits, but every step escalated to the cloud uses "Computer credits at the standard rate" (the Portable Computer article, last modified September 15, 2026). A closed agent metered by its vendor puts the pricing, the pause and the balance on the vendor's side. On your own stack, model spend is an itemized bill from the provider you chose.

### The hosting you cannot choose

"Computer normally runs in a secure cloud sandbox", the help center states, with the data in that same Personal Cloud Sandbox. The local variant changes the address without changing the ownership. Portable Computer runs "the model, orchestrator, scheduler, and sandbox on your own device instead", but the software is still Perplexity's app on an NVIDIA DGX Spark or an RTX GPU with 24 GB of VRAM or more, under a Pro or Max subscription (the Portable Computer article, last modified September 15, 2026). Between the hosted product and the local app, no Perplexity page describes running the agent in software you build or control. Running Perplexity's app on your own GPU is a convenience tier, not a system a team administers. SPACE does not change that; it hosts sandboxes, and an agent still has to drive them.

### The models you cannot swap

Model choice is a menu Perplexity controls. The Portable Computer article lists two local models, PPLX 27B and Qwen 27B, with Nemotron marked as coming soon, and cloud escalation offers "a choice of 15+ models" (last modified September 15, 2026). Picking within the menu is different from bringing your own provider, and no Perplexity page documents customer-supplied keys. When a model is deprecated or repriced, the change arrives through the product rather than through a file you edit. The routing policy sits in exactly the layer a sandbox release cannot touch.

## What opening SPACE changes, and what it leaves closed

The release deserves real credit: a hardened sandbox under a permissive license, with documentation, and cloud providers named in the announcement already deploying it. For a developer building an agent, it is a foundation worth adopting. For a Perplexity Computer customer, it changes almost nothing about the five limitations above, because all five live in the layer Perplexity kept. The table separates what the release answers from what only ownership answers.

| Limitation | Does the SPACE release fix it | What owning the agent layer changes |
| --- | --- | --- |
| Source | No: the repository holds the sandbox, not the agent | The agent is code you read and change |
| Memory export | No: saved memory stays a product feature | Memory lives in files in your repo |
| Credits | No: metering belongs to the subscription | Spend becomes your provider's itemized bill |
| Self-hosting | No: SPACE hosts sandboxes, not the agent | The whole stack runs on your network |
| Models | No: the menu ships inside the closed agent | The agent you own calls what you configure |

## What owning the agent layer fixes

Kortix is the open-source AI Operating System: agents, skills, memory, and connectors in one git repo you own, with each session running on its own cloud computer (the Kortix docs, read 18 October 2026). It is the recommendation for teams that need the agent layer in their own hands, and each limitation above maps to a structural answer in Kortix's own words:

- The source you could not read: "Open source. Read it, fork it, audit it." ([Kortix on GitHub](https://github.com/kortix-ai/suna)) An agent in Kortix is a file in the repo, so behavior, triggers and permissions sit in front of you as text.
- The hosting you could not choose: "Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free." Self-hosting is the product's own install path, not a closed app pointed at approved hardware.
- The isolation SPACE proved matters: "One isolated sandbox per session. Each session has its own isolated machine and branch." Kortix ships the same per-session isolation attached to an agent you own rather than one you rent.
- The trust the meter cannot buy: "Session work reaches `main` through a change request. Merge is default-deny for agents." Oversight is a diff a person approves, where Perplexity's model is steering the worker while it runs.

For the full side-by-side with sources attached, the site keeps a [Kortix vs Perplexity Computer comparison](https://opensourceperplexitycomputer.com/kortix-vs-perplexity-computer) current. If the conclusion is that the agent layer should be yours, [Try Kortix](https://kortix.com).

## Frequently asked questions

### Is Perplexity Computer open source after the SPACE release?

No. The October 15, 2026 release is SPACE, the sandbox platform, and SPACE itself is open source under the Apache License, Version 2.0. Perplexity Computer's agent, its model routing, the connectors and the saved memory stay closed subscription features, and none of them appear in the repository.

### Why is Perplexity Computer closed?

Perplexity sells Computer as a subscription product available to Pro and Max subscribers, and its own announcement offers developers the sandbox, not the agent. No Perplexity page states a reason for keeping the agent closed; a hosted worker billed in credits is what the company's pages describe, and that is the whole answer its documentation gives.
