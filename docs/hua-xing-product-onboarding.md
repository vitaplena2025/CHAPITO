# Hua Xing Product Onboarding

## Purpose

This record documents the first Hua Xing product load into CHAPITO and the conventions that future transaction imports must follow.

## Target

- Supabase project: `CHAPITO`
- Project ref: `ejkvymlezbqvzsmwejca`
- Product table: `public.skus`
- Company value: `Hua Xing`
- Source file: `ITEMS HUA XING.xls`
- Load date: `2026-07-28`

## Canonical SKU Rule

All Hua Xing source SKU identifiers receive the prefix `HX-` before they are stored in CHAPITO.

| Source SKU | Canonical SKU | Item | Case pack |
| --- | --- | --- | ---: |
| `001` | `HX-001` | AJO CON CASCARA 20/1 LIBRA | 20 |
| `002` | `HX-002` | AJO CON CASCARA 40/8ONZAS | 40 |
| `003` | `HX-003` | AJO PELADO 4/5 LIBRAS | 4 |
| `004` | `HX-004` | AJO PELADO 20/1 LIBRA | 20 |
| `PP206` | `HX-PP206` | HINGED CLAMSHELL 6"X 9" | 250 |
| `PP601` | `HX-PP601` | HINGED CLAMSHELL 6"X6" | 250 |
| `PP801` | `HX-PP801` | HINGED CLAMSHELL 8"X 8" | 150 |
| `PP803` | `HX-PP803` | HINGED CLAMSHELL 8"X 8"X 3 | 150 |

The eight records were verified in `public.skus` with `active = true`. The unprefixed identifiers no longer remain for Hua Xing. No sales referenced either version of these identifiers when the prefix was applied.

## Fields Pending

The official source did not include the following values, so they remain `NULL`:

- `brand`
- `landed_cost`
- `notes`

Product images were not supplied.

## Transaction-Onboarding Rules

Hua Xing products are sold by the same representatives who sell Vitaplena products. Transactions may occur at existing Vitaplena points of sale, in different departments within those locations, or at additional customers.

Before loading Hua Xing transactions:

1. Prefix each source SKU with `HX-`.
2. Match the resulting SKU to `public.skus`.
3. Match seller names to the canonical CHAPITO sales-representative values.
4. Match customer-name variants to existing canonical Vitaplena customers when they represent the same point of sale.
5. Validate chain, channel, and department.
6. Create new customers only for genuinely unmatched points of sale.
7. Preserve `company = Hua Xing` on the transaction.
8. Produce a review list for any unmatched SKU, customer, or seller.

## Information Still Required

- Landed cost by SKU
- Brand by SKU
- Product photographs
- Hua Xing transaction file
- Customer alias mapping
- Canonical seller-name validation
- Chain, channel, and department validation

The detailed workbook audit is stored at `outputs/hua-xing-product-onboarding/Hua_Xing_Product_Import_Audit.xlsx`.
