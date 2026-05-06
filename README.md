# VA MAVERIC — AWS Research Platform Case Study

An interactive architecture case study showing the modernization of the Veterans Affairs MAVERIC research enclave platform — originally architected June 2020 in collaboration with the AWS Solution Design team for the Million Veteran Program, modernized May 2026 with current AWS service names, governance patterns, and endpoint controls.

**Live at:** https://shidokan.github.io/maveric/

**Companion case study (Azure):** https://shidokan.github.io/mosiac/

---

## What's in here

```
index.html           — the case study (React app, self-contained)
maveric-before.png   — original 2020 architecture diagram
README.md            — this file
```

The HTML is fully self-contained — React 18 from CDN, Babel for in-browser JSX compilation, Google Fonts for typography. No build step. Open `index.html` in any modern browser.

---

## Deploying to a fresh GitHub repo

Since this is a new empty repo at `https://github.com/shidokan/maveric.git`, the full first-push sequence is:

```
cd path/to/your/local/maveric/folder
git init
git add .
git commit -m "Initial commit: AWS MAVERIC research platform case study"
git branch -M main
git remote add origin https://github.com/shidokan/maveric.git
git push -u origin main
```

Then enable GitHub Pages:

1. Go to the repo on GitHub → **Settings → Pages**
2. **Source: Deploy from a branch**
3. **Branch: main** · **Folder: / (root)**
4. **Save**

Wait 60–90 seconds and the page will be live at `https://shidokan.github.io/maveric/`.

---

## What the page covers

**16 clickable services** organized across the modernized 2026 architecture, each with role description, what changed since 2020, and interview talking points:

- **Platform Account services** — CloudFront + Lambda@Edge, API Gateway + Lambda, DynamoDB, Cognito, OpenSearch (renamed from Elasticsearch), CloudTrail Lake (replaces QLDB), S3 + Lake Formation, Glue + Step Functions, HealthOmics (new), QuickSight + Q
- **Researcher Account services** — WorkSpaces (new VDI layer), SageMaker Unified Studio
- **Org-level services** — Control Tower, DataZone (new), IAM Identity Center (renamed from AWS SSO), KMS

**Three big architectural calls in the modernization** that the page surfaces:

1. **Amazon QLDB is being retired** (end-of-support July 31, 2025) — the original audit ledger replaced by AWS CloudTrail Lake
2. **Amazon WorkSpaces added as the endpoint-control layer** — the original design relied on per-account isolation but didn't enforce no-exfiltration at the endpoint, which is the gap most auditors flag now
3. **AWS HealthOmics added for the genomic data tier** — didn't exist in 2020 (launched November 2022), but it's the natural 2026 home for the omics workloads MAVERIC was built around

**Three-personas section** preserves the Administrator / Data Steward / Researcher role model from the original requirements doc, updated to reference the 2026 services.

**About section** highlights two patterns from the original design that aged remarkably well:

- The multi-account-per-researcher topology — now AWS Control Tower's standard playbook
- The manual data extraction approval workflow — anticipated AWS Clean Rooms by three years

It also makes the explicit bridge to health-plan analytics: replace MAVERIC with a payer's analytics estate, replace genomic researchers with claims analysts, and the architectural shape transfers directly.

---

## Cross-navigation to the Azure case study

The header includes a navigation pill ("Azure case study ↗") that links to https://shidokan.github.io/mosiac/. To add a matching reverse link on the Azure page, see the snippet in that repo's README.

---

## Customizing content

The page is driven by JavaScript data blocks near the top of the `<script>` tag. Look for:

- **`SERVICES`** — the object holding deep-dive content for each clickable service (role, evolution, talking points, optional compliance/positioning notes)
- **`CHANGES`** — the four-column grid summarizing what was kept, renamed, added, and dropped

Edit these to tune narrative for a specific interview or audience.

---

## Using this in interviews

A few practical notes:

- The page works fully offline once loaded. If you're interviewing on a system that blocks CDNs, open it in a browser before the call to warm the cache.
- The three-view toggle (Before · After · Side-by-side) lets you walk an interviewer through the evolution without scrolling around.
- The service modal is keyboard-navigable: Tab to focus a node, Enter or Space to open, Escape to close.
- Modal content is intentionally substantive — long enough to be useful as a leave-behind, short enough to read on screen during a conversation.

---

## Credit

Architecture originally designed in June 2020 in collaboration with the AWS Solution Design team for the VA Million Veteran Program — including the multi-account research enclave pattern, three-persona role model, and data extraction approval workflow.

Modernized May 2026 to reflect current AWS service names, governance patterns, and endpoint controls.

— John Carlo Cueva, Principal Cloud Architect · Chicago
