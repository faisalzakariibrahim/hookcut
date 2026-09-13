# Viralyte — operator notes

**Product name:** Viralyte  
**Canonical site:** [https://viralyte.app](https://viralyte.app)  
**Upstream:** fork of [mutonby/openshorts](https://github.com/mutonby/openshorts) (core app MIT)

## Monetization notes

- **Own billing on MIT core.** You may monetize a hosted service built on the MIT-licensed core (self-hosted app outside `cloud/`) with your own billing.
- **Do NOT use upstream `cloud/` for third-party SaaS** without a commercial license. The [`cloud/`](cloud/LICENSE) directory (billing, managed keys, hosted-service infrastructure behind `BILLING_ENABLED`) is source-available under the upstream commercial license — readable and self-hostable for personal/internal use, but not for offering to third parties as a paid/hosted service without permission.
- For a commercial license covering `cloud/`, contact: **jc.caverogracia@gmail.com**

When `BILLING_ENABLED` is truthy, the optional `cloud/` billing stack is active (Stripe Checkout + Customer Portal). Self-hosting the core app never requires this.

### Plans (overview)

| Plan | Monthly minutes (approx.) | Notes |
|------|---------------------------|--------|
| **Free** | **20 min** / month | Watermark; no credit card |
| **Starter** | 100 min | Paid; no watermark |
| **Creator** | 300 min | Paid; no watermark |
| **Pro** | 750 min | Paid; no watermark |

Prices are resolved from Stripe at runtime — amounts are not hard-coded in env.

### Stripe `lookup_key`

Subscription and top-up **Prices** are looked up by stable Stripe `lookup_key` values (no price IDs in environment config), for example:

- Subscriptions: `starter_monthly`, `starter_yearly`, `creator_monthly`, `creator_yearly`, `pro_monthly`, `pro_yearly`
- Top-ups: `topup_60`, `topup_200`

Ensure those keys exist and are active on the Stripe account before enabling billing in production.

## Brand checklist (light)

- Public product name: **Viralyte**
- Site: **viralyte.app**
- Dashboard package name: `viralyte-app`
- Repo rename and asset/logo swaps are out of scope for this light rebrand
