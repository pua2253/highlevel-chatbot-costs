# gohighlevel ai chatbot setup: the no-code build steps, what each route really costs, and when native Conversation AI isn't enough

Type "gohighlevel ai chatbot setup" into Google and you get two very different kinds of answer: GoHighLevel's own help docs walking you through Conversation AI, and a stack of tutorials promising a human-like agent in five minutes. Both are describing real things, but they're describing different products with different bills attached.

That's the part most guides skip. HighLevel now ships its own chatbot builder inside every account, and it also hosts a marketplace full of third-party agents. The setup steps look similar on the surface — connect something, write instructions, point it at a calendar — but the cost model, the ceiling, and the amount of babysitting afterward are not.

Here's how both routes actually work, in the order you'd do them.

## The two routes, and how to tell which one you're on

Everything in GoHighLevel splits into one of these:

- **Native Conversation AI.** Built into the platform under AI Agents. Billed by tokens per message, or covered by an AI Employee add-on at $50 or $97 per month per location.
- **A third-party agent layer.** A separate platform that logs into your sub-accounts and answers the same conversations. You pay a subscription plus per-message usage. CloseBot is the best-known name here — it's the most-installed sub-account app in the HighLevel marketplace, according to CloseBot's own comparison page — and it's what most of this article uses as the concrete example, because the pricing and setup steps are public.

If you only need appointment booking and FAQ answers for one business, the native route is free-ish and gets you there. If the conversation *is* the product — agency clients, high lead volume, real qualification logic — you end up in the second category sooner or later.

## Route A: setting up the native Conversation AI bot

The flow inside HighLevel is short. Open **AI Agents → Conversation AI → + Create Bot**, then pick one of three setup methods:

1. **Guided Form Setup.** Best for lead capture, general Q&A, and simple booking. Choose a bot type, pick a Brand Voice, fill in Bot Settings and Bot Goals, save. Beginner-friendly and structured; not much room for weird edge cases.
2. **Prompt Based Bot.** You write the prompts yourself and get model selection, custom personality, and actions like human handover, workflow triggers, stop bot, and conversation summaries. Prompt quality drives the result — HighLevel's own docs point you at their AI prompting guide before you start.
3. **Flow Based Builder.** Visual branching for multi-step qualification and nurturing. You launch the flow builder, configure tone, personality, intent, and business context, then wire actions and appointment options.

One detail that catches people: a new bot is often set to **Off**. You have to switch it to **Suggestive** (your team reviews and sends each reply) or **Auto-Pilot** (it sends them itself). Skipping that step is the single most common reason someone finishes "setup" and sees nothing happen.

GoHighLevel's documentation is explicit that you should test lead capture, FAQs, booking, unknown questions, and workflow behavior before flipping to Auto-Pilot. Unknown-question alerts can be emailed to selected users, which matters — an agent that invents an answer is worse than one that hands off.

**The cost side.** Conversation AI is billed on tokens: input tokens (customer messages, conversation history, instructions, knowledge base content) and output tokens (the replies). HighLevel's published rates run from $0.25 per million input tokens on a mini-class model up to $2.00, and from $1.60 to $10.00 per million output tokens depending on the model. Two conversations of the same length can land at different prices because token volume varies.

If you'd rather not watch a meter, HighLevel sells flat add-ons: **AI Employee Growth at $50/month per enabled location** (1,000 Conversation AI agent responses, 100 Voice AI minutes, overages at pay-as-you-go rates) and **AI Employee Unlimited at $97/month per enabled location** (unlimited Conversation AI and Voice AI, subject to fair use). Agent Studio stays pay-per-token on every plan, including the unlimited one.

## Route B: setting up a CloseBot agent on a HighLevel sub-account

CloseBot doesn't replace the CRM — it sits on top of it and answers the text channels already flowing through it. Its docs describe the connection as a click-to-connect OAuth flow, and the whole first-time path is short:

1. Create the account (the free plan needs no card).
2. Go to **Sources**, click **New Source**, choose **HighLevel Sub-Account**, then **Connect**.
3. An OAuth window opens from HighLevel. Approve the permissions and pick the sub-account you want to connect.
4. Back in CloseBot, tick **Allow CloseBot to create/update fields** — this is what lets the agent write custom properties. Skip it and your qualification data has nowhere to land.
5. Click **Add Source**. If the Sources list appears, the connection worked.
6. Registering auto-creates a starter agent for your industry. You then connect the source to that agent, or build your own job flow from scratch, a template library, or an AI prompt.

CloseBot markets a "48-second setup" and documents it as: register, add a source, connect the source to the auto-created starter agent. That's accurate for what it is — a simple Q&A agent answering a live sub-account. It is not the same thing as a qualification-and-booking agent trained on your offer. An independent review published in August 2026 puts realistic initial configuration at **5 to 10 hours** once you factor in knowledge base building and webhook wiring. Budget for the second number if you're selling this to a client.

For anything beyond Q&A, the object you're actually building is a **job flow**, and CloseBot V2's **Agent Node** is the piece that does the heavy lifting. An agent node has its own instructions (split into named sections), tools, and exits, and it can replace the older objective, statement, conversation, and booking nodes. You reference variables with `@`, tools with `@@`, and exits with `@@@` inside the instructions, and exits can also trigger on tag rules in the CRM — so a contact who already booked can be pulled out of the QUALIFY node automatically.

If your customer conversation needs a held-open door, you need to know about one thing: **👀 [👉 compare CloseBot's current plans and included message volume before you pick a tier](https://app.closebot.com/a?fpr=li87)**. The number of messages bundled at base price is the difference between a predictable bill and a wallet top-up in week two.

### The GoHighLevel side you still have to set up

CloseBot answers conversations; it doesn't configure your CRM. Before going live, you still need:

- A **booking calendar** in the sub-account the agent can write to, with your availability and buffers correct.
- **Custom fields** for whatever the agent is supposed to capture, mapped so the data is usable.
- **Tags** for handoff logic — the docs show tag-driven examples like handing off to sales on a qualified lead, sending a scheduling link, or pausing the bot entirely.
- **Workflow triggers** in HighLevel if you want CRM automations firing off the back of what the agent does.

Teams that skip this half are the ones who report an agent that "works but doesn't book anything" — the conversation is fine, the plumbing isn't connected.

## What each route is actually good at

|  | Native Conversation AI | CloseBot |
| --- | --- | --- |
| Where it lives | Inside HighLevel | On top of HighLevel (also HubSpot, LeadConnector, custom CRMs) |
| Build method | Guided form, prompts, or flow builder | Drag-and-drop job flows, Agent Nodes, tools |
| Billing | Token cost, or $50/$97 per month add-ons | Subscription + per-message usage (business base price includes message costs) |
| Agency white-label & rebilling | Not its purpose | Flat agency plan with Stripe rebilling and a white-label client portal |
| Entry cost | Free to try on any plan | Free plan: 1 agent, 100 messages/month |

Community sentiment on the native option is mixed but not hostile. In a r/gohighlevel thread comparing the two, one commenter's read was that GHL's conversation AI "has gotten better but it's still pretty clunky for SMS specifically." That's one person's experience, not a benchmark. But it matches the general shape of the comparison: HighLevel builds an all-in-one platform, where features tend to land at surface level first; CloseBot is a single-purpose product, and its comparison page argues exactly that, including the claim that HighLevel's AI previously capped custom field updates at 20 while CloseBot has always updated unlimited fields.

## Pricing: every plan CloseBot currently shows

CloseBot publishes two tracks — business and agency — on the same plans page. Here's the full set as listed, with the important caveats underneath.

| Plan | Best for | Included messages | Price | Billing | Get started |
| --- | --- | --- | --- | --- | --- |
| **Free** | Testing the platform or very low lead volume | 100/month (overage $0.08 each) | $0 | Forever, no card | [Start on the free plan](https://app.closebot.com/a?fpr=li87) |
| **Core (Business)** | Running your own pipeline | Base cap 500/month, message costs included in the price | $64/mo (annual option: $53/mo, billed $640/yr) | Monthly or annual, cancel anytime | [Pick the business plan tier](https://app.closebot.com/a?fpr=li87) |
| **Core (Agency)** | Agencies building and reselling agents for clients | Unlimited, billed $0.012 per message and fully rebillable | $397/mo | Monthly, month-to-month | [Set up the agency plan](https://app.closebot.com/a?fpr=li87) |
| **Growth** | SLAs, compliance, quarterly audits, high volume | Custom | Custom quote | Custom | [Request the Growth tier quote](https://app.closebot.com/a?fpr=li87) |

Things worth knowing before you buy:

- **The business tier scales with volume.** The plans page slider runs from 100 up to 100K+ monthly messages. A third-party breakdown from August 2026 lists the monthly-price ladder as $64 (up to 500 messages), $84 for 1,000, $109 for 2,000, $176 for 5,000, $454 for 20,000, $806 for 50,000, and roughly $1,059 for 100,000. Treat those higher-tier numbers as a guide and confirm on the page, since that slider moves.
- **One message isn't always one message.** Use the Agent Node's "unlimited potential" options — many tools, unlimited instruction size — and billing shifts to token-based segments. CloseBot's own FAQ says you may be charged more segments per message in that configuration.
- **Free plan limits:** 1 agent, 1 user seat, 1 MB of knowledge storage, and unlimited account connections. That last one is handy: you can point a single test agent at several sub-accounts.
- **Everything is month-to-month, and there are no refunds.** You get a 7-day trial of any paid plan and a free plan that stays free under 100 messages a month. Do your evaluation there.
- **No bring-your-own API key.** CloseBot's FAQ frames this as a security decision. On paid plans you select from the providers CloseBot works with — OpenAI, Anthropic, Gemini, and Grok — with automatic fallback if your primary model fails.
- **Agency extras:** $5 per additional user seat, storage at $0.006 per MB per day, and rebilling through your own Stripe account. CloseBot charges the agency $0.012 per message; you set your client markup.

That last point is the real agency math. If you resell 10,000 messages a month at a 2x markup, the message line alone produces $120 of margin, before what you charge for the build.

## So which one should you set up?

Three questions settle it, and none of them are about features:

1. **Whose pipeline is it?** Your own business → Core business plan, message costs baked in. Client sub-accounts with rebilling → the agency plan is the only one that supports the white-label portal and Stripe rebilling.
2. **How many conversations per month?** Under 100, stay free. A few hundred, the $64 base cap is roughly right. Four figures a month is where the business ladder starts mattering and where you should re-check the slider before committing.
3. **Do you have someone to maintain it?** Agents drift when the knowledge base goes stale. The review that estimated 5 to 10 hours of setup also flagged ongoing knowledge base upkeep as the main failure mode — an agent answering from an outdated document is worse than no agent.

And if your answer is "I just need FAQ answers and simple booking for one location," stop reading and use the native bot. It's included in the platform you already pay for, the setup is genuinely 20 minutes, and the token bill on low volume is pennies.

The moment the answer becomes "I need this conversation to qualify, handle objections, and book a high-intent appointment while I sleep," the native route's ceiling shows up — and that's the gap CloseBot was built to fill.

### A few questions that come up mid-setup

**Does CloseBot connect to Instagram and WhatsApp directly?** No. It connects to your CRM, and picks up whatever channels that CRM supports. If Instagram DMs flow into your HighLevel Conversations inbox, the agent can answer them there. There's no standalone Instagram or WhatsApp connection inside CloseBot itself, so a business with no CRM would have to add one first.

**Can the agent update HighLevel contact records?** Yes, if you ticked "Allow CloseBot to create/update fields" during the source connection, and you've mapped the fields you care about. Tag changes can also drive exits.

**What happens when the agent doesn't know an answer?** There's a Smart FAQ tool that flags the question rather than inventing a response. You answer it once, and CloseBot can follow up with every lead who asked.

**Is there a contract?** No. Plans run month to month, and CloseBot's FAQ states plainly that refunds aren't offered — which is why the free plan and the 7-day trial exist.

**Has anyone checked whether it's actually good?** CloseBot holds a 4.8 out of 5 rating on G2, and published vendor figures include over a million booked appointments, roughly 150,000 messages a day, and 99.99% uptime. Those are the company's own numbers, not audited ones. The more useful signal is that the platform shows up repeatedly in agency discussions as the recommended upgrade path when the native bot stops keeping up.

Start with the free plan, connect one real sub-account, and watch what the agent does with a genuine lead before you change anything about your billing. Setup is the easy part. 👉 [Building your first CloseBot agent takes one OAuth click and a free account](https://app.closebot.com/a?fpr=li87).
