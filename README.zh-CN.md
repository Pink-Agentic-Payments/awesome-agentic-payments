# Awesome Agentic AI Payments（AI 智能体支付资源精选） [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

[English](./README.md) | 简体中文

精选 AI 智能体（AI agent）安全完成支付所需的协议、MCP 服务器、钱包、消费管控工具与研究资料。

本列表由 Pink Agentic AI Payment（PinkWallet）团队维护；条目按实际价值收录，包括竞争对手。

以下每个链接均于 2026-09-29 直接抓取并确认可正常访问（完整审计记录见本仓库的 [`link-check.csv`](./link-check.csv)）。每条描述均取自对应链接页面本身——具体每条描述来自哪个 URL，同样可在该文件中查到。

另见：[Agentic Payments 时间线（2024–2026）](./TIMELINE.zh-CN.md)：从 MCP 发布到 x402 Foundation 成立，30 个带日期、带来源链接的事件。

## 目录

- [协议与标准](#协议与标准)
- [支付类 MCP 服务器](#支付类-mcp-服务器)
- [智能体钱包与支付基础设施](#智能体钱包与支付基础设施)
- [消费管控与防护措施](#消费管控与防护措施)
- [SDK、示例与教程](#sdk示例与教程)
- [研究、报告与数据集](#研究报告与数据集)
- [文章与指南](#文章与指南)
- [贡献指南](#贡献指南)
- [许可证](#许可证)

## 协议与标准

- [a2a-x402](https://github.com/google-a2a/a2a-x402) — 一个将 Google 的 Agent Payments Protocol（AP2，智能体支付协议）与 x402 协议对接、用于稳定币结算的扩展，据称是"in collaboration with Coinbase, Ethereum Foundation, MetaMask and other leading organizations"（译：与 Coinbase、Ethereum Foundation、MetaMask 等领先机构合作）打造，旨在提供"a production-ready solution for agent-based crypto payments."（译：一个可用于生产环境的智能体加密货币支付方案）。
- [Agent Payments Protocol (AP2)](https://github.com/google-agentic-commerce/AP2) — 使用"Mandates — tamper-proof, cryptographically-signed digital contracts that serve as verifiable proof of a user's instructions."（译：Mandates——防篡改、经密码学签名的数字合约，作为用户指令的可验证证明）。已于 2026-04-28 由 Google 捐赠给 FIDO Alliance；相关公告称此举"ensures AP2 remains platform-agnostic and community-led."（译：确保 AP2 保持平台中立、由社区主导）。采用 Apache-2.0 许可证。
- [Agentic Commerce Protocol (ACP)](https://agenticcommerce.dev) — "An interaction model and open standard for connecting buyers, their AI agents, and businesses to complete purchases seamlessly."（译：一种交互模型与开放标准，用于连接买家、买家的 AI 智能体与商家，实现无缝完成购买。）由 Stripe 与 OpenAI 共同开发；其参考实现仓库的 README 称该规范"is maintained by OpenAI and Stripe and is currently in beta."（译：由 OpenAI 与 Stripe 共同维护，目前处于 beta 阶段）。采用 Apache-2.0 许可证。
- [Machine Payments Protocol (MPP)](https://mpp.dev) — "MPP lets agents pay for services on the web, extensible to any payment method."（译：MPP 让智能体能够为网络上的服务付费，且可扩展到任意支付方式。）由 Stripe 于 2026-03-18 发布，"co-authored by Tempo and Stripe."（译：由 Tempo 与 Stripe 共同撰写）。提供 TypeScript、Python、Rust、Go 与 Ruby 的 SDK。
- [Mastercard Agent Pay](https://newsroom.mastercard.com/news/press/2025/april/mastercard-unveils-agent-pay-pioneering-agentic-payments-technology-to-power-commerce-in-the-age-of-ai) — 发布于 2025-04-29。"Consumers will have complete control over what the agent is allowed to purchase on their behalf."（译：消费者将对智能体可代其购买的内容拥有完全控制权。）建立在 Mastercard 现有的、用于移动端非接触支付与卡片保留信息（card-on-file）的代币化技术之上。
- [Universal Commerce Protocol (UCP)](https://github.com/universal-commerce-protocol/ucp) — "Specification and documentation for the Universal Commerce Protocol (UCP)."（译：Universal Commerce Protocol（UCP，通用商务协议）的规范与文档。）由 Google 于 2026-01-11 发布，"in collaboration with industry leaders including Shopify, Etsy, Wayfair, Target, and Walmart,"（译：与 Shopify、Etsy、Wayfair、Target、Walmart 等行业领先企业合作），并"compatible with Agent Payments Protocol (AP2)."（译：与 Agent Payments Protocol（AP2）兼容）。采用 Apache-2.0 许可证。
- [Visa Trusted Agent Protocol (TAP)](https://usa.visa.com/about-visa/newsroom/press-releases.releaseId.21716.html) — 发布于 2025-10-14，与 Cloudflare 共同开发，Visa 感谢了"insightful feedback from other early partners including Adyen, Ant International, Checkout.com, Coinbase, CyberSource, Elavon, Fiserv, Microsoft, Nuvei, Shopify, Stripe and Worldpay."（译：来自 Adyen、Ant International、Checkout.com、Coinbase、CyberSource、Elavon、Fiserv、Microsoft、Nuvei、Shopify、Stripe 与 Worldpay 等其他早期合作伙伴的深刻反馈）。这是一种密码学消息签名标准（RFC 9421），商家用它在结账前验证智能体的身份；它本身并不转移资金。
- [x402](https://docs.x402.org/faq) — "An open-source protocol that turns the dormant HTTP 402 Payment Required status code into a fully-featured, onchain payment layer for APIs, websites, and autonomous agents."（译：一个开源协议，将闲置已久的 HTTP 402 Payment Required 状态码，变为面向 API、网站与自主智能体的功能完善的链上支付层。）自 2026-07-14 起在 Linux Foundation 治理下作为 x402 Foundation 运作，已有 40 个成员组织。采用 Apache-2.0 许可证。

## 支付类 MCP 服务器

官方厂商 MCP 服务器，其自身文档描述的工具可创建或移动支付对象（退款、代付、订单、支付链接）。

- [Adyen MCP server](https://docs.adyen.com/development-resources/mcp-server) — 仅限本地运行的服务器，覆盖 Adyen 的 Checkout API 与 Management API；在其 GitHub 仓库中被标注为 alpha 阶段。文档页面给出的示例提示词包括："Refund order #12345"（译：为订单 #12345 退款）与"Create a €50 payment link for order #ABC789."（译：为订单 #ABC789 创建一个 50 欧元的支付链接）。
- [Checkout.com MCP Server](https://www.checkout.com/docs/developer-resources/checkout-com-mcp-server) — 托管式服务器（沙盒与生产环境端点各自独立），被描述为"production-ready source of truth,"（译：可用于生产环境的权威数据源），提供的工具包括创建/获取支付链接、获取支付详情、列出实体与撤销授权（Voids）等。访问权限是受限的："you can only perform payment operations that your Dashboard user has permissions to action."（译：你只能执行你的 Dashboard 用户已被授权的支付操作）。
- [Mollie MCP Server](https://docs.mollie.com/docs/mollie-mcp-server) — 远程服务器（mcp.mollie.com/mcp），覆盖 Payments、Payment links、Customers、Subscriptions、Mandates、Captures、Balances 与 Settlements；用户通过 Mollie 自己的 OAuth 2.0 浏览器登录进行身份验证，而不是把 API key 输入到 AI 工具中。
- [PayPal Agent Toolkit & MCP Server](https://paypal.gitbook.com/agent-toolkit-and-mcp-server) — 本地（`npx -y @paypal/mcp`）或远程 MCP 服务器；环境可设置为 SANDBOX 或 PRODUCTION。文档记录的工具包括 create_invoice、create_order 与 create_refund。
- [Razorpay MCP Server](https://razorpay.com/docs/developer-tools/mcp-server/) — 托管式或自托管（Docker）服务器，提供 35 个以上工具，包括 capture_payment、create_refund 与 create_instant_settlement；支持 READ_ONLY 标志，将服务器限制为只读操作。
- [Square MCP Server](https://developer.squareup.com/docs/mcp) — 托管式（mcp.squareup.com/mcp）或本地服务器，提供对 Square API 中"customers, orders, items, and more"（译：客户、订单、商品等）的访问。Square"maintains an allowlist of MCP clients in order to protect against malicious client registration attempts."（译：维护一份 MCP 客户端白名单，以防范恶意客户端注册行为）。目前处于 Beta 阶段。
- [Stripe MCP Server](https://docs.stripe.com/mcp) — 托管式（mcp.stripe.com）或本地服务器，提供通用的 API 读写工具。像退款、对外付款这样的敏感写操作，需要人工通过一个链接进行确认，该链接若未获批准会在 24 小时后失效。自 2026-10-31 起，"Stripe MCP no longer accepts full-access secret keys or restricted API keys without the Agent tag."（译：Stripe MCP 将不再接受未带 Agent 标签的完全访问密钥或受限 API 密钥）。

## 智能体钱包与支付基础设施

- [Airwallex AgentOS](https://www.airwallex.com/docs/developer-tools/ai/agentos) — 面向生产环境 Airwallex 账户的 CLI 加 MCP 连接器。默认情况下，"AgentOS components do not initiate money-out actions (transfers, FX conversions, or payouts) on your behalf"（译：AgentOS 组件默认不会代你发起资金转出操作，如转账、换汇或代付）；写操作工具需要明确确认。
- [Circle Agent Wallets](https://developers.circle.com/agent-stack/agent-wallets) — 允许开发者"set USDC spending limits for outbound transfers and x402 payments,"（译：为对外转账与 x402 支付设置 USDC 消费限额），这些限额"can be time-bound,"（译：可设定时间范围），另外提供钱包/合约白名单与黑名单，并在链上提交前进行制裁名单筛查。
- [Coinbase Agentic Wallet / AgentKit](https://docs.cdp.coinbase.com/agentic-wallet/cli/welcome) — 供 AI 智能体持有并发送 USDC 的钱包 CLI，具备"configurable caps per session and per transaction"（译：可按会话与按交易配置的上限），并对所有转账自动进行 OFAC 制裁名单筛查。
- [Crossmint Agent Checkouts](https://docs.crossmint.com/agents/overview) — 远程 MCP 服务器（create-order、check-order、get-usd-balance），一旦环境变量从 test 切换到 prod，即可执行真实购买。根据[结账 MCP 服务器的 README](https://github.com/Crossmint/mcp-crossmint-checkout)，商品会以加急配送方式送达，并生成收据、代收销售税。
- [Locus](https://paywithlocus.com/) — "One Account for Every AI Agent Tool"（译：一个账户，适用于每一个 AI 智能体工具）：让"an AI agent one connection to a catalog of paid APIs and proprietary data sources,"（译：一个 AI 智能体只需一次连接，即可访问一整套付费 API 与专有数据源目录），并可"from one balance instead of relying on separate provider accounts, subscriptions, and API keys."（译：使用同一个余额支付，而不必依赖各家分散的服务商账户、订阅与 API key）。
- [Payman (Genie)](https://github.com/PaymanAI/genie-mcp-stdio) — 一个本地 stdio 桥接程序，连接到 Payman 的远程 Genie MCP 服务器，通过带 PKCE 的 OAuth 2.0 进行身份验证。官方 README 记录了一个 `ask_genie` 自然语言工具，以及若干自助账户管理工具；并未列出支付执行类工具。
- [Pink Agentic AI Payment](https://pinkwallet.com/agentic/?utm_source=github&utm_medium=awesome-list) — "Lets AI agents connect and pay through MCP while a policy engine enforces each customer's spending rules before any payment executes."（译：让 AI 智能体通过 MCP 连接并完成支付，同时由策略引擎在任何支付执行前，强制执行每个客户设定的消费规则。）MCP 服务器 + 支付执行前强制生效的消费规则（early access——暂无公开沙盒环境或安装包；可加入等候名单）。*（本列表维护方的项目）*
- [Skyfire (KYA / KYAPay)](https://docs.skyfire.xyz/docs/developer-documentation) — 身份加支付的令牌协议："each buyer agent has a wallet, funded by the user,"（译：每个买方智能体都拥有一个由用户注资的钱包），该钱包向卖方 MCP 服务器、API 或网站出示已签名的 JWT 令牌（kya、pay、kya-pay）以完成交易。
- [Tempo Wallet CLI](https://tempo.xyz/developers/docs/wallet/use-with-agents) — 命令行钱包，"each wallet can have multiple access keys with independent spending limits."（译：每个钱包可拥有多个访问密钥，各自具有独立的消费限额）。`--max-spend` 会"stop[s] if the request would exceed a spend cap,"（译：在请求将超出消费上限时予以阻止），`--dry-run` 则可在提交资金前预览费用并验证请求。

## 消费管控与防护措施

主要作用是在智能体支付前强制执行预算、白名单或审批环节的产品与库——独立于任何单一支付通道。

- [agent-verifier-mcp](https://github.com/goodmeta/agent-verifier-mcp) — "MCP server for AI agent spending limits. One config change to add budget enforcement."（译：面向 AI 智能体消费限额的 MCP 服务器。只需一次配置变更即可加入预算强制执行。）实现了一套 Budget Authority Protocol（create_budget、check_budget、settle、release、refund），明确做到与支付通道无关："works with x402, credit cards, MPP, bank transfers."（译：可配合 x402、信用卡、MPP、银行转账使用）。
- [Authoryze](https://authoryze.ai/) — "The authorization and control layer for AI agent payments."（译：面向 AI 智能体支付的授权与管控层。）标语："Your agent asks. Your rules decide. Approved purchases get a single-use card."（译：你的智能体发起请求，你的规则做决定，获批的购买会拿到一张单次使用的卡。）注：域名 agentpays.dev（在第三方 MCP 目录中发现的一个名称）目前会重定向（HTTP 308，于 2026-09-29 检查）到这个正在运营的站点；我们未能在任何地方确认这两个名称是否指向同一家公司。
- [PayAgents](https://payagents.io/) — "Payment Orchestration for AI Agents & MCP Servers."（译：面向 AI 智能体与 MCP 服务器的支付编排。）面向比特币闪电网络（L402）与 Base 链 USDC（x402）支付的策略管控型钱包，提供按交易、按天、按 30 天的消费上限，目的地白名单/黑名单以及审计追踪。
- [PolicyLayer](https://policylayer.com/) — "The system of record for AI agent authority."（译：AI 智能体权限的记录系统。）作为任意 MCP 服务器前的代理层运行，依据一份 YAML 策略文件评估每一次 tools/call 请求，据此放行、拦截、限速，或将其转交人工审批。
- [SpendNod](https://www.spendnod.com/) — "Open-source authorization gateway for AI agents."（译：面向 AI 智能体的开源授权网关。）采用 MIT 许可证并可自托管；智能体在每次购买前调用 `authorize_transaction` 工具，该请求会依据消费阈值、供应商黑名单、每日上限与品类规则进行核验。

## SDK、示例与教程

可运行的代码，而不仅是规范文档。

- [Coinbase AgentKit](https://github.com/coinbase/agentkit) — "Every AI Agent deserves a wallet."（译：每个 AI 智能体都应有一个钱包。）开源 SDK，用于为 AI 智能体提供链上钱包与支付操作能力。
- [Locus Pro Plugin](https://github.com/locus-technologies/locus-pro-plugin) — 官方插件，其 README 建议智能体"quote significant calls with `estimate_cost` first, and to confirm with you before unusually large spends,"（译：对重要调用先用 `estimate_cost` 进行报价，并在异常大额支出前与你确认），并指出"spend limits and approvals are configured per workspace in the dashboard."（译：消费限额与审批在仪表盘中按工作区配置）。
- [MPP Quickstart](https://mpp.dev/quickstart/) — "Get started with MPP in minutes"（译：几分钟内即可上手 MPP）——Machine Payments Protocol 的官方快速入门指南，提供 TypeScript、Python、Rust、Go 与 Ruby 的 SDK。
- [Pink agent-spending-limit-example](https://github.com/Pink-Agentic-Payments/agent-spending-limit-example) — "Runnable example: enforce an AI agent's spending cap, allowlist, approval threshold and idempotency BEFORE a payment executes (Node, no deps)."（译：可运行示例：在支付执行前强制实施 AI 智能体的消费上限、白名单、审批阈值与幂等性（Node，无外部依赖）。）*（本列表维护方的项目）*
- [x402 Quickstart for Buyers](https://docs.x402.org/getting-started/quickstart-for-buyers) — "This guide walks you through how to use x402 to interact with services that require payment,"（译：本指南将带你了解如何使用 x402 与需要付费的服务进行交互，）包括跨 EVM、Solana、Aptos 与 Algorand 的钱包签名器设置。
- [x402 Quickstart for Sellers](https://docs.x402.org/getting-started/quickstart-for-sellers) — "This guide walks you through integrating with x402 to enable payments for your API or service,"（译：本指南将带你了解如何集成 x402，为你的 API 或服务启用付费能力，）包括面向 Express、Next.js、Hono、Fastify、Go 与 Python 的框架专属中间件。

## 研究、报告与数据集

- [AP2 announcement (Google Cloud)](https://cloud.google.com/blog/products/ai-machine-learning/announcing-agents-to-payments-ap2-protocol) — Google Cloud 关于 Agent Payments Protocol 的发布公告，说明 Intent Mandate"provides the auditable context for the entire interaction"（译：为整个交互过程提供可审计的上下文），而 Cart Mandate"creates a secure, unchangeable record of the exact items and price."（译：为具体商品与价格创建一份安全、不可更改的记录）。
- [AP2 joins FIDO Alliance (Google)](https://blog.google/products-and-platforms/platforms/google-pay/agent-payments-protocol-fido-alliance/) — Google 于 2026-04-28 发布的公告，称将所有权转移至 FIDO Alliance"ensures AP2 remains platform-agnostic and community-led"（译：确保 AP2 保持平台中立、由社区主导）。
- [Agent Spending Controls Crosswalk](https://github.com/Pink-Agentic-Payments/agent-spending-controls-crosswalk) — 一份厂商中立的对照表，梳理 14 家支付服务商与协议如何限制 AI 智能体的花费：共 43 行引用数据，涵盖具体字段名称、单位与执行点，每行均附原文引用来源（CC BY 4.0）。*（本列表维护方的项目）*
- [Agentic Commerce Protocol announcement (Stripe)](https://stripe.com/blog/developing-an-open-standard-for-agentic-commerce) — Stripe 与 OpenAI 关于 ACP 的发布公告，将其描述为支持"programmatic commerce flows between buyers, AI agents, and businesses"（译：买家、AI 智能体与商家之间的程序化商务流程），同时商家"is the merchant of record."（译：作为记录商户）。
- [Machine Payments Protocol announcement (Stripe)](https://stripe.com/blog/machine-payments-protocol) — Stripe 于 2026-03-18 发布的 MPP 公告，"co-authored by Tempo and Stripe,"（译：由 Tempo 与 Stripe 共同撰写），支持"stablecoins as well as fiat with cards and buy now, pay later payment methods via Shared Payment Tokens (SPTs)."（译：稳定币，以及通过 Shared Payment Tokens（SPTs）实现的、含卡与先买后付方式的法币支付）。
- [Pink agent-spending-policy](https://github.com/Pink-Agentic-Payments/agent-spending-policy) — 草案 v0.1，一套与厂商无关的 JSON Schema，用于描述 AI 智能体的支出策略（额度、白名单、审批阈值），并逐字段映射到 14 家支付服务商的原生设置，引用自同系列的 crosswalk 数据集。非标准（CC BY 4.0 文档 / Apache-2.0 代码）。*（本列表维护方的项目）*
- [Pink agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) — "Can AI agents actually pay? 16 payment providers scored on 7 agent-readiness dimensions, evidence-linked (CC BY 4.0)."（译：AI 智能体真的能付款吗？对 16 家支付服务商在 7 个智能体就绪度维度上进行评分，并附证据链接（CC BY 4.0）。）共 228 项检查，每项均附证据 URL、原文引用与访问日期。*（本列表维护方的项目）*
- [Universal Commerce Protocol announcement (Google)](https://developers.googleblog.com/under-the-hood-universal-commerce-protocol-ucp/) — Google 于 2026-01-11 发布的 UCP 公告，称其为"an open-source standard designed to power the next generation of agentic commerce,"（译：一个旨在驱动下一代智能体商务的开源标准），与 Shopify、Etsy、Wayfair、Target、Walmart 共同开发。
- [x402 Foundation operational launch (Linux Foundation)](https://www.linuxfoundation.org/press/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications) — x402 治理权移交给 Linux Foundation 的公告："40 organizations have joined as members,"（译：已有 40 家组织加入成为会员），其中 Premier 会员包括 Adyen、AWS、American Express、Circle、Coinbase、Google、Mastercard、Shopify、Stripe 与 Visa。

## 文章与指南

- [Managing agent spend (MPP)](https://mpp.dev/guides/managing-agent-spend) — 官方指南，介绍如何借助 Tempo access keys 在 MPP 支付之上叠加消费管控，并给出一个实例：某密钥"can spend up to 10 USDC per day and only transfer USDC to one recipient."（译：每日最多可花费 10 USDC，且只能向一个收款方转账 USDC）。
- [OpenAI Commerce docs](https://developers.openai.com/commerce/) — "The infrastructure between merchants and shoppers in ChatGPT,"（译：ChatGPT 中商家与购物者之间的基础设施，）覆盖 Agentic Commerce Protocol（ACP），将其定义为"an open standard that serves as the connective layer between merchants and ChatGPT users."（译：作为商家与 ChatGPT 用户之间连接层的开放标准）。
- [Stripe Agentic Commerce docs](https://docs.stripe.com/agentic-commerce) — "Agentic commerce uses AI agents to support transactions between buyers and sellers, and to let agents transact on behalf of the people they serve,"（译：智能体商务借助 AI 智能体支持买卖双方之间的交易，并让智能体代表其所服务的人完成交易，）涵盖通过智能体销售（UCP/ACP）与接受机器支付（MPP/x402）两方面。
- [UCP merchant integration guide (Google)](https://developers.google.com/merchant/ucp) — "The Universal Commerce Protocol (UCP) is an open standard designed for the future of commerce, empowering you to turn AI interactions into instant sales,"（译：Universal Commerce Protocol（UCP）是一项为商务未来而设计的开放标准，让你能够把 AI 交互转化为即时销售，）依托现有 Merchant Center 账户的商品数据源（shopping feeds）。
- [x402 vs AP2 vs ACP: Which Agent Payment Protocol Should You Build On?](https://pinkwallet.com/agentic/learn/x402-vs-ap2-vs-acp/?utm_source=github&utm_medium=awesome-list) — "x402, AP2 and ACP solve different layers of AI agent payments: pay-per-request stablecoin settlement, proof of user authorization, and in-chat checkout."（译：x402、AP2 与 ACP 分别解决 AI 智能体支付中的不同层次：按请求付费的稳定币结算、用户授权证明，以及聊天内结账。）*（本列表维护方的项目）*

## 贡献指南

欢迎提交 Pull Request。完整贡献指南见 [CONTRIBUTING.md](./CONTRIBUTING.md)。要被收录，链接必须满足：

- **公开可访问** — 所链接页面阅读时没有登录墙。
- **可正常打开** — 在你提交时能正常返回 HTTP 200（或最终跳转到 200 的重定向）。
- **相关** — 与 AI 智能体完成支付相关：涉及支付的协议、MCP 服务器或 SDK，消费管控/防护类产品，或专门针对智能体支付的研究/分析（不包括泛金融科技或泛 AI 智能体工具）。
- **有该链接页面自身的引用作为依据** — 不接受营销式改写，不接受来源页面未提及的说法。

请在对应分类下按字母顺序的正确位置提交 PR，添加你的条目，并附上一句取自所链接页面、事实性、非营销性质的描述。如果你所在的公司被本列表描述，且认为某一行有误或已过时，请在 PR 中说明——我们欢迎更正，并会对照你自己的页面重新核实。

## 许可证

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

在法律允许的范围内，本列表作者已放弃对本作品的一切版权及相关或邻接权利。详见 [LICENSE](./LICENSE)（CC0-1.0）。

