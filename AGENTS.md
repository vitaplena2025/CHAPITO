# CHAPITO Development Guide

## Project Overview

CHAPITO is a Sales Intelligence Dashboard for a CPG distribution company.

The application is currently built as a single-page dashboard.

Main application:

- index.html

Admin interface:

- admin.html

---

## Supabase Architecture

CHAPITO depends on two separate Supabase projects. Never confuse their responsibilities.

Primary application database:

- Project name: CHAPITO
- Project ref: `ejkvymlezbqvzsmwejca`
- Use for sales, customers, SKUs, companies, upload logs, and market-universe data.

External SKU image source:

- Project name: App de Merchandisers
- Project ref: `uxdjiqysuurfgfvjxcqg`
- Use only for product-image storage unless explicitly instructed otherwise.
- SKU images live in the public `fotos` bucket under `skus/`.
- Expected object path: `fotos/skus/<normalized-sku>.jpg`.

Normalize SKU image filenames by converting the SKU to lowercase and removing accents or diacritics. Preserve the SKU's remaining characters.

Before changing Supabase data or storage:

- verify the target project
- verify the target table, bucket, and object path
- prefer read-only inspection before writes
- limit changes to the explicitly requested records or objects
- verify the result after writing

Never commit API keys, database passwords, service-role keys, access tokens, connection strings, or other secrets. Project refs are identifiers and may be documented.

---

## Company and SKU Conventions

CHAPITO stores canonical SKU identifiers in `public.skus` and uses the same identifiers when loading `public.sales`.

Hua Xing rules:

- Prefix every Hua Xing source SKU with `HX-`.
- Preserve the complete source SKU after the prefix, including leading zeros and letters.
- Example mappings: `001` becomes `HX-001`; `PP206` becomes `HX-PP206`.
- Store `company = Hua Xing`.
- Apply the prefix before matching or inserting Hua Xing sales.
- When product images are provided, use the canonical prefixed SKU in the normalized object filename, for example `fotos/skus/hx-001.jpg`.

Hua Xing sales are handled by the same sellers who handle Vitaplena and may occur at the same points of sale, in different departments, or at additional customers. Before loading transactions:

- match seller names to the existing canonical sales-representative values
- match Hua Xing customer variants to existing canonical Vitaplena customers when they represent the same point of sale
- create a new customer only when no canonical match exists
- retain `Hua Xing` as the transaction company
- document unmatched customers, sellers, and SKUs before the final load

The initial onboarding record is in `docs/hua-xing-product-onboarding.md`.

---

## General Rules

Always preserve existing functionality unless explicitly requested.

Never remove features without asking.

Maintain responsive behavior.

Keep the UI consistent with the current design language.

Prefer improving existing components instead of replacing them.

---

## JavaScript

Use modern vanilla JavaScript.

Avoid unnecessary external libraries.

Always destroy and recreate Chart.js charts correctly.

Avoid memory leaks.

Keep code readable and modular.

---

## HTML

Maintain semantic HTML.

Avoid duplicate IDs.

Keep accessibility in mind.

---

## CSS

Maintain current visual style.

Use existing spacing and typography.

Do not introduce random colors.

---

## Dashboard Rules

Executive Scorecard

Portfolio

Customers

Sales Team

Opportunities

Compare

Canceladas

must continue working after every change.

---

## Git

Before finishing:

- check for JavaScript errors
- verify charts render correctly
- verify filters still work
- verify no console errors

Never commit automatically unless requested.

Never push automatically unless requested.

---

## Responses

Explain briefly what changed.

List modified files.

Mention any assumptions.
