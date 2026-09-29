# Awesome Agentic AI Payments [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of protocols, MCP servers, wallets, spending controls and research for letting AI agents make payments safely.

Maintained by the team behind Pink Agentic AI Payment (PinkWallet); entries are selected on merit and include competitors.

Every link below was fetched directly and confirmed live on 2026-09-29 (see [`link-check.csv`](./link-check.csv) in this repo for the full audit trail). Every description is sourced from the linked page itself — see the same file for exactly which URL each description came from.

## Contents

- [Protocols & Standards](#protocols--standards)
- [Payment MCP Servers](#payment-mcp-servers)
- [Agent Wallets & Payment Infrastructure](#agent-wallets--payment-infrastructure)
- [Spending Controls & Guardrails](#spending-controls--guardrails)
- [SDKs, Examples & Tutorials](#sdks-examples--tutorials)
- [Research, Reports & Datasets](#research-reports--datasets)
- [Articles & Guides](#articles--guides)
- [Contributing](#contributing)
- [License](#license)

## Protocols & Standards

- [a2a-x402](https://github.com/google-a2a/a2a-x402) — An extension that wires Google's Agent Payments Protocol (AP2) to the x402 protocol for stablecoin settlement, built "in collaboration with Coinbase, Ethereum Foundation, MetaMask and other leading organizations" to give "a production-ready solution for agent-based crypto payments."
- [Agent Payments Protocol (AP2)](https://github.com/google-agentic-commerce/AP2) — Uses "Mandates — tamper-proof, cryptographically-signed digital contracts that serve as verifiable proof of a user's instructions." Donated by Google to the FIDO Alliance on 2026-04-28; the announcement says the move "ensures AP2 remains platform-agnostic and community-led." Apache-2.0.
- [Agentic Commerce Protocol (ACP)](https://agenticcommerce.dev) — "An interaction model and open standard for connecting buyers, their AI agents, and businesses to complete purchases seamlessly." Co-developed by Stripe and OpenAI; the reference repo's README states the spec "is maintained by OpenAI and Stripe and is currently in beta." Apache-2.0.
- [Machine Payments Protocol (MPP)](https://mpp.dev) — "MPP lets agents pay for services on the web, extensible to any payment method." Announced by Stripe on 2026-03-18, "co-authored by Tempo and Stripe." SDKs in TypeScript, Python, Rust, Go and Ruby.
- [Mastercard Agent Pay](https://newsroom.mastercard.com/news/press/2025/april/mastercard-unveils-agent-pay-pioneering-agentic-payments-technology-to-power-commerce-in-the-age-of-ai) — Announced 2025-04-29. "Consumers will have complete control over what the agent is allowed to purchase on their behalf." Built on Mastercard's existing tokenization used for mobile contactless payments and card-on-file.
- [Universal Commerce Protocol (UCP)](https://github.com/universal-commerce-protocol/ucp) — "Specification and documentation for the Universal Commerce Protocol (UCP)." Announced 2026-01-11 by Google "in collaboration with industry leaders including Shopify, Etsy, Wayfair, Target, and Walmart," and "compatible with Agent Payments Protocol (AP2)." Apache-2.0.
- [Visa Trusted Agent Protocol (TAP)](https://usa.visa.com/about-visa/newsroom/press-releases.releaseId.21716.html) — Announced 2025-10-14, developed with Cloudflare, with Visa crediting "insightful feedback from other early partners including Adyen, Ant International, Checkout.com, Coinbase, CyberSource, Elavon, Fiserv, Microsoft, Nuvei, Shopify, Stripe and Worldpay." A cryptographic message-signing standard (RFC 9421) merchants use to verify an agent's identity before checkout; it does not itself move money.
- [x402](https://docs.x402.org/faq) — "An open-source protocol that turns the dormant HTTP 402 Payment Required status code into a fully-featured, onchain payment layer for APIs, websites, and autonomous agents." Operational under Linux Foundation governance since 2026-07-14 as the x402 Foundation, with 40 member organizations. Apache-2.0.

## Payment MCP Servers

Official vendor MCP servers whose own documentation describes tools that create or move payment objects (refunds, payouts, orders, payment links).

- [Adyen MCP server](https://docs.adyen.com/development-resources/mcp-server) — Local-only server covering Adyen's Checkout API and Management API; labeled alpha on its GitHub repo. Example prompts on the docs page: "Refund order #12345" and "Create a €50 payment link for order #ABC789."
- [Checkout.com MCP Server](https://www.checkout.com/docs/developer-resources/checkout-com-mcp-server) — Hosted server (separate sandbox and production endpoints) described as a "production-ready source of truth," with tools including Create/Get Payment Link, Get Payment Details, List Entities and Voids. Access is scoped: "you can only perform payment operations that your Dashboard user has permissions to action."
- [Mollie MCP Server](https://docs.mollie.com/docs/mollie-mcp-server) — Remote server (mcp.mollie.com/mcp) covering Payments, Payment links, Customers, Subscriptions, Mandates, Captures, Balances and Settlements; users authenticate via Mollie's own OAuth 2.0 browser login rather than entering an API key into the AI tool.
- [PayPal Agent Toolkit & MCP Server](https://paypal.gitbook.com/agent-toolkit-and-mcp-server) — Local (`npx -y @paypal/mcp`) or remote MCP server; environment can be set to SANDBOX or PRODUCTION. Documented tools include create_invoice, create_order and create_refund.
- [Razorpay MCP Server](https://razorpay.com/docs/developer-tools/mcp-server/) — Hosted or self-hosted (Docker) server with 35+ tools including capture_payment, create_refund and create_instant_settlement; supports a READ_ONLY flag to restrict the server to read-only operations.
- [Square MCP Server](https://developer.squareup.com/docs/mcp) — Hosted (mcp.squareup.com/mcp) or local server giving access to "customers, orders, items, and more" across the Square API. Square "maintains an allowlist of MCP clients in order to protect against malicious client registration attempts." Currently in Beta.
- [Stripe MCP Server](https://docs.stripe.com/mcp) — Hosted (mcp.stripe.com) or local server exposing generic API read/write tools. Sensitive writes such as refunds and outbound payments require human confirmation via a URL that expires after 24 hours if unapproved. From 2026-10-31, "Stripe MCP no longer accepts full-access secret keys or restricted API keys without the Agent tag."

## Agent Wallets & Payment Infrastructure

- [Airwallex AgentOS](https://www.airwallex.com/docs/developer-tools/ai/agentos) — CLI plus MCP connector for a production Airwallex account. "AgentOS components do not initiate money-out actions (transfers, FX conversions, or payouts) on your behalf" by default; write tools require explicit confirmation.
- [Circle Agent Wallets](https://developers.circle.com/agent-stack/agent-wallets) — Lets developers "set USDC spending limits for outbound transfers and x402 payments," with limits that "can be time-bound," plus wallet/contract allow- and blocklists and sanctions screening before onchain submission.
- [Coinbase Agentic Wallet / AgentKit](https://docs.cdp.coinbase.com/agentic-wallet/cli/welcome) — Wallet CLI for AI agents to hold and send USDC, with "configurable caps per session and per transaction" and automatic OFAC sanctions-list screening on all transfers.
- [Crossmint Agent Checkouts](https://docs.crossmint.com/agents/overview) — Remote MCP server (create-order, check-order, get-usd-balance) that executes real purchases once the environment variable is switched from test to prod. Per the [checkout MCP server's README](https://github.com/Crossmint/mcp-crossmint-checkout), the item is delivered with expedited shipping, a receipt is generated and sales tax is collected.
- [Locus](https://paywithlocus.com/) — "One Account for Every AI Agent Tool": a single MCP connection to a catalog of 40+ pay-per-use APIs billed against one prepaid workspace credit balance funded via Stripe Checkout, with USDC/x402 as one settlement rail among the providers it aggregates.
- [Payman (Genie)](https://github.com/PaymanAI/genie-mcp-stdio) — A local stdio bridge to Payman's remote Genie MCP server, authenticated via OAuth 2.0 with PKCE. The official README documents an `ask_genie` natural-language tool plus self-service account-management tools; it does not itemize payment-execution tools.
- [Pink Agentic AI Payment](https://pinkwallet.com/agentic/?utm_source=github&utm_medium=awesome-list) — "Lets AI agents connect and pay through MCP while a policy engine enforces each customer's spending rules before any payment executes." MCP server + spending rules enforced before a payment executes (early access — no public sandbox or package yet; join the waitlist). *(maintained by the list authors)*
- [Skyfire (KYA / KYAPay)](https://docs.skyfire.xyz/docs/developer-documentation) — Identity-plus-payment token protocol: "each buyer agent has a wallet, funded by the user," which presents signed JWT tokens (kya, pay, kya-pay) to seller MCP servers, APIs or websites to transact.
- [Tempo Wallet CLI](https://tempo.xyz/developers/docs/wallet/use-with-agents) — Command-line wallet where "each wallet can have multiple access keys with independent spending limits." `--max-spend` "stop[s] if the request would exceed a spend cap," and `--dry-run` previews cost and validates a request before committing funds.

## Spending Controls & Guardrails

Products and libraries whose primary purpose is enforcing a budget, allowlist or approval step in front of agent payments — independent of any one payment rail.

- [agent-verifier-mcp](https://github.com/goodmeta/agent-verifier-mcp) — "MCP server for AI agent spending limits. One config change to add budget enforcement." Implements a Budget Authority Protocol (create_budget, check_budget, settle, release, refund) that is explicitly rail-agnostic: "works with x402, credit cards, MPP, bank transfers."
- [Authoryze](https://authoryze.ai/) — "The authorization and control layer for AI agent payments." Tagline: "Your agent asks. Your rules decide. Approved purchases get a single-use card." Note: this is the live site that the domain agentpays.dev (a name found in third-party MCP directories) now redirects to (HTTP 308, checked 2026-09-29); we could not confirm anywhere whether the two names refer to the same company.
- [PayAgents](https://payagents.io/) — "Payment Orchestration for AI Agents & MCP Servers." Policy-controlled wallet for Bitcoin Lightning (L402) and Base-chain USDC (x402) payments, with per-transaction, per-day and per-30-day spend caps, destination allow/denylists and an audit trail.
- [PolicyLayer](https://policylayer.com/) — "The system of record for AI agent authority." Acts as a proxy in front of any MCP server, evaluating every tools/call request against a YAML policy file and forwarding, blocking, rate-limiting, or routing it to a human for approval.
- [SpendNod](https://www.spendnod.com/) — "Open-source authorization gateway for AI agents." MIT-licensed and self-hosted; agents call an `authorize_transaction` tool before every purchase, checked against spending thresholds, vendor blocklists, daily caps and category rules.

## SDKs, Examples & Tutorials

Runnable code, not just specs.

- [Coinbase AgentKit](https://github.com/coinbase/agentkit) — "Every AI Agent deserves a wallet." Open-source SDK for giving AI agents an onchain wallet and payment actions.
- [Locus Pro Plugin](https://github.com/locus-technologies/locus-pro-plugin) — Official plugin whose README recommends agents "quote significant calls with `estimate_cost` first, and to confirm with you before unusually large spends," and notes "spend limits and approvals are configured per workspace in the dashboard."
- [MPP Quickstart](https://mpp.dev/quickstart/) — "Get started with MPP in minutes" — official quickstart for the Machine Payments Protocol, with SDKs in TypeScript, Python, Rust, Go and Ruby.
- [Pink agent-spending-limit-example](https://github.com/Pink-Agentic-Payments/agent-spending-limit-example) — "Runnable example: enforce an AI agent's spending cap, allowlist, approval threshold and idempotency BEFORE a payment executes (Node, no deps)." *(maintained by the list authors)*
- [x402 Quickstart for Buyers](https://docs.x402.org/getting-started/quickstart-for-buyers) — "This guide walks you through how to use x402 to interact with services that require payment," including wallet signer setup across EVM, Solana, Aptos and Algorand.
- [x402 Quickstart for Sellers](https://docs.x402.org/getting-started/quickstart-for-sellers) — "This guide walks you through integrating with x402 to enable payments for your API or service," including framework-specific middleware for Express, Next.js, Hono, Fastify, Go and Python.

## Research, Reports & Datasets

- [AP2 announcement (Google Cloud)](https://cloud.google.com/blog/products/ai-machine-learning/announcing-agents-to-payments-ap2-protocol) — Google Cloud's announcement of the Agent Payments Protocol, explaining that an Intent Mandate "provides the auditable context for the entire interaction" and a Cart Mandate "creates a secure, unchangeable record of the exact items and price."
- [AP2 joins FIDO Alliance (Google)](https://blog.google/products-and-platforms/platforms/google-pay/agent-payments-protocol-fido-alliance/) — Google's 2026-04-28 announcement that transitioning ownership to the FIDO Alliance "ensures AP2 remains platform-agnostic and community-led."
- [Agentic Commerce Protocol announcement (Stripe)](https://stripe.com/blog/developing-an-open-standard-for-agentic-commerce) — Stripe and OpenAI's announcement of ACP, describing it as enabling "programmatic commerce flows between buyers, AI agents, and businesses" while the business "is the merchant of record."
- [Machine Payments Protocol announcement (Stripe)](https://stripe.com/blog/machine-payments-protocol) — Stripe's 2026-03-18 announcement of MPP, "co-authored by Tempo and Stripe," supporting "stablecoins as well as fiat with cards and buy now, pay later payment methods via Shared Payment Tokens (SPTs)."
- [Pink agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) — "Can AI agents actually pay? 13 payment providers scored on 7 agent-readiness dimensions, evidence-linked (CC BY 4.0)." 185 total checks, each with an evidence URL, direct quote and access date. *(maintained by the list authors)*
- [Universal Commerce Protocol announcement (Google)](https://developers.googleblog.com/under-the-hood-universal-commerce-protocol-ucp/) — Google's 2026-01-11 announcement of UCP as "an open-source standard designed to power the next generation of agentic commerce," developed with Shopify, Etsy, Wayfair, Target and Walmart.
- [x402 Foundation operational launch (Linux Foundation)](https://www.linuxfoundation.org/press/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications) — Announcement that x402 governance moved to the Linux Foundation: "40 organizations have joined as members," including Premier members Adyen, AWS, American Express, Circle, Coinbase, Google, Mastercard, Shopify, Stripe and Visa.

## Articles & Guides

- [Managing agent spend (MPP)](https://mpp.dev/guides/managing-agent-spend) — Official guide on layering spending controls on top of MPP payments using Tempo access keys, with a worked example: a key that "can spend up to 10 USDC per day and only transfer USDC to one recipient."
- [OpenAI Commerce docs](https://developers.openai.com/commerce/) — "The infrastructure between merchants and shoppers in ChatGPT," covering the Agentic Commerce Protocol (ACP) as "an open standard that serves as the connective layer between merchants and ChatGPT users."
- [Stripe Agentic Commerce docs](https://docs.stripe.com/agentic-commerce) — "Agentic commerce uses AI agents to support transactions between buyers and sellers, and to let agents transact on behalf of the people they serve," covering both selling through agents (UCP/ACP) and accepting machine payments (MPP/x402).
- [UCP merchant integration guide (Google)](https://developers.google.com/merchant/ucp) — "The Universal Commerce Protocol (UCP) is an open standard designed for the future of commerce, empowering you to turn AI interactions into instant sales," using an existing Merchant Center account's shopping feeds.
- [x402 vs AP2 vs ACP: Which Agent Payment Protocol Should You Build On?](https://pinkwallet.com/agentic/learn/x402-vs-ap2-vs-acp/?utm_source=github&utm_medium=awesome-list) — "x402, AP2 and ACP solve different layers of AI agent payments: pay-per-request stablecoin settlement, proof of user authorization, and in-chat checkout." *(maintained by the list authors)*

## Contributing

Pull requests welcome. To be added, a link must be:

- **Public** — no login wall to read the page that's being linked.
- **Working** — resolves with a normal HTTP 200 (or a redirect that ends in one) at the time you submit.
- **Relevant** — about AI agents making payments: a protocol, an MCP server or SDK that touches payments, a spending-control/guardrail product, or research/analysis about agent payments specifically (not general fintech or general AI agent tooling).
- **Backed by a quote from the linked page itself** — no marketing paraphrase, no claims the source page doesn't make.

Open a PR adding your entry in the correct alphabetical position within its section, with a one-line, factual, non-promotional description sourced from the page you're linking. If you work at a company being described and think a line is wrong or out of date, please say so in the PR — corrections are welcome and will be re-verified against your own page.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the list authors have waived all copyright and related or neighboring rights to this work. See [LICENSE](./LICENSE) (CC0-1.0).
