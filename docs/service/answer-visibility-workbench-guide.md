# Answer Visibility Workbench — Operator Guide

The Workbench is a standalone delivery tool for the **Answer Visibility AEO service**. Use it to move a client from intake to a repeatable baseline, implementation backlog, and client report.

## Start a client engagement

1. Open [Answer Visibility Workbench](./answer-visibility-workbench.html) in a current desktop browser. It does not need installation, a server, or an account.
2. Select **Client setup** and fill in the company, website, product, buyer, approved proof, priority markets, business goal, and approver.
3. Select the answer/search platforms included in the client's paid scope. Record the client's crawler policy before proposing any `robots.txt`, CDN, or hosting change.
4. Save a JSON backup from **Data → Download workspace backup**. Store it in your normal client file system, subject to your client data policy.
5. In **Question set**, add questions based on actual prospect conversations, sales calls, support questions, comparison pages, and the client’s market. The editable starter set is a seed, not finished research; replace all bracketed text.
6. Agree with the client which products, competitors, markets, questions, and platforms form the sample. Keep them stable for subsequent reporting.

## Run the baseline and delivery cycle

### Baseline (week 1–2)

- Run every agreed question manually in each agreed platform. Use a consistent geography, language, and logged-in/logged-out context as far as practicable.
- In **Answer checks**, record brand inclusion, answer accuracy, whether the company's own source was cited, competitors named, source URLs, and a short observation.
- Audit crawl/index access, existing product pages, approved claims, third-party profiles, and available Search Console/analytics data.
- Create the client’s prioritized actions in **Action plan**. Assign a person and due date; separate client approvals from provider work.
- Build the paid **Visibility Baseline** report before proposing a sprint or retainer.

### Improve (weeks 3–8)

- Start with high-priority factual, crawl, and page-quality issues. Use the client’s subject-matter expert and approved source material.
- Improve the pages buyers use to discover, compare, and evaluate the product. Preserve existing accurate information and add original proof, clear product details, and helpful context.
- For changes to technical access, crawl rules, analytics, or claims, get the client's approval and record the decision/evidence in an action item.
- Update action status as work moves from open to in progress to done. Add the resulting URL or ticket in the evidence field.

### Monitor and report (monthly; formal review at day 90)

- Re-run the same question/platform sample. Add dated observations rather than overwriting earlier checks.
- Review brand mention, client-source citation, and accuracy rates alongside the individual examples. These rates are simple descriptions of the saved sample, not a platform ranking.
- Compare Search Console and analytics trends, ChatGPT referrals where present, landing-page engagement, and qualified leads if the client has reliable tracking.
- In **Reports**, enter an executive summary, next-cycle priorities, and sample/data limitations. Use **Print / save PDF** or **Download Markdown** to deliver the update.
- Use the 90-day review to renew, narrow, or revise scope based on the evidence and the client's business goal.

## What each workspace section does

| Section | Purpose | Output |
|---|---|---|
| **Overview** | Current sample metrics, 6-month mention trend, delivery progress, upcoming actions, recent checks | Working status snapshot |
| **Client setup** | Client facts, approved claims, reporting scope, selected platforms, and guardrails | Client source of truth |
| **Question set** | Stable buyer-intent prompt library grouped by category and priority | Reusable monitoring sample |
| **Answer checks** | Dated manual observations from answer/search platforms | Evidence log |
| **Action plan** | Prioritized, assigned work with due dates and evidence | Delivery backlog |
| **Reports** | Sample metrics, observation table, priority work, interpretation, and caveats | Printable or Markdown client report |

## Delivery playbook and scope handoff

Use the commercial package in [AEO Service Offer](./aeo-service-offer.md) when scoping and selling. Suggested client path:

1. **Visibility Baseline — $2,000 one-time:** a two-week diagnostic with up to 40 questions and 3 answer/search experiences.
2. **AEO Foundation Sprint — $7,500 one-time:** six weeks of priority implementation.
3. **Answer Visibility Partner — $3,500/month, 3-month minimum:** up to 40 questions and 3 platforms, monthly analysis, up to 2 priority page improvements or briefs, and a review meeting.
4. **Market Leader — $6,000/month, 3-month minimum:** expanded monitoring and delivery for larger or multi-market scopes.

Confirm the actual limits in the signed proposal. Keep software subscriptions, engineering work, extra brands/languages, paid media, PR placement fees, and out-of-scope content separately priced. Do not let the interface imply work that is not in the contract.

## Data, automation, and limitations

- Workspaces are saved to the browser's `localStorage`. Data is not synced to a server, shared with clients, or backed up automatically. Export a JSON file regularly and transfer it using your approved storage method.
- Importing a backup replaces the current in-browser workspace. Export the current workspace first if you need to preserve it.
- The app does **not** query ChatGPT, Google, Perplexity, Bing, Gemini, analytics, Search Console, a CMS, or a CRM. An operator runs the questions and enters observations manually.
- The app does **not** provide automated crawler audits, prompt scheduling, multi-user permissions, billing, client login, or server-side backups. Use a secure hosted system and add integrations before making those part of a commercial promise.
- Do not store passwords, API keys, sensitive personal information, confidential customer data, or material the client has not authorized you to retain.
- Answer outputs vary by platform, geography, personalization, and time. The recorded sample can show directional patterns. It cannot guarantee future mentions, citations, rankings, traffic, or revenue.

## Suggested client-facing explanation

“We repeat a fixed set of buyer questions across the agreed answer/search platforms and record what appears, how accurately your company is described, and which sources are cited. We then improve the highest-value content and technical gaps we can substantiate, and compare later observations with the baseline. This is a directional visibility sample, so we report it alongside site analytics and qualified outcomes; we do not guarantee individual platform placements.”

