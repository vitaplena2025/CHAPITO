# CHAPITO

Sales Intelligence Dashboard for CPG Distribution.

## Main Files

- index.html
- admin.html

## Features

- Executive Scorecard
- Portfolio Analytics
- Customer Intelligence
- Sales Team Performance
- Opportunity Engine
- Compare Studio
- Cancelled Sales Analysis

## Technology

- HTML
- CSS
- Vanilla JavaScript
- Chart.js
- Supabase

## Supabase Architecture

CHAPITO uses two separate Supabase projects:

### CHAPITO

- Project name: `CHAPITO`
- Project ref: `ejkvymlezbqvzsmwejca`
- Role: Primary application database
- Stores sales, customers, SKUs, companies, upload history, and market-universe data.

### App de Merchandisers

- Project name: `App de Merchandisers`
- Project ref: `uxdjiqysuurfgfvjxcqg`
- Role: External source for SKU product images
- SKU images are stored in the public `fotos` bucket under `skus/`.
- Expected object path: `fotos/skus/<normalized-sku>.jpg`

SKU filenames use lowercase characters and omit accents or diacritics. For example:

```text
TÖS-0186 → fotos/skus/tos-0186.jpg
```

The project refs are identifiers, not credentials. API keys, database passwords, service-role keys, access tokens, and other secrets must never be committed to the repository.

## Company and SKU Conventions

CHAPITO supports products and sales from multiple operating companies.

- Vitaplena SKU identifiers keep their existing canonical values.
- Hua Xing SKU identifiers use the canonical prefix `HX-`.
- A raw Hua Xing SKU such as `001` is stored as `HX-001`.
- Hua Xing transaction imports must apply the same prefix before matching sales to `public.skus`.
- Hua Xing customers and sales representatives must be matched to the existing canonical CHAPITO records whenever they represent the same Vitaplena customer or seller.
- The sale's company remains `Hua Xing` so company-level reporting stays accurate.

The initial Hua Xing product onboarding record is documented in [docs/hua-xing-product-onboarding.md](docs/hua-xing-product-onboarding.md).

## Repository

Primary development happens through Codex using Git.
