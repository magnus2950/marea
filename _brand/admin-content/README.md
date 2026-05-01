# MAREA · Admin setup checklist

Alt der ligger her skal oprettes i Shopify Admin (manuel copy-paste eller via API). Temafiler er allerede i repo'et — det er kun **data** (sider, produkter, menuer, indstillinger) der mangler.

Rækkefølge der skal følges:

## 1 · Sprog & valuta
**Settings → Store details**
- Currency: `DKK` (Danish krone)
- Unit system: Metric
- Time zone: `(GMT+01:00) Copenhagen`
- Default weight unit: `g`

**Settings → Languages**
- Add language: **Danish**
- Set as default
- Publish (kunder ser dansk)
- Optional: behold engelsk som "unpublished"

## 2 · Kollektioner
**Products → Collections → Create**

Opret disse kollektioner (alle automatic, conditions justeres senere):

| Title | Handle | Beskrivelse |
|---|---|---|
| Alle smykker | `all` | (auto-genereret af Shopify, eksisterer allerede) |
| Nyheder | `nyheder` | Conditions: Tag = `new` |
| Bestsellers | `bestsellers` | Conditions: Tag = `bestseller` |
| Halskæder | `halskaeder` | Conditions: Product type = `Halskæde` |
| Øreringe | `oreringe` | Conditions: Product type = `Ørering` |
| Armbånd | `armbaand` | Conditions: Product type = `Armbånd` |
| Ringe | `ringe` | Conditions: Product type = `Ring` |
| SS26 Launch | `ss26-launch` | Conditions: Tag = `ss26` |
| Waterproof | `waterproof` | Conditions: Tag = `waterproof` |

## 3 · Sider (Pages)
**Online Store → Pages → Add page**

Opret én side pr. fil i `pages/`-mappen. Title og handle står øverst i hver fil. Kopiér indhold direkte ind i Rich Text-editoren (HTML-fanen kan også bruges).

## 4 · Blog & indlæg
**Online Store → Blog posts**

Først: opret blog "Journal" (handle: `journal`).
Derefter opret hvert blogindlæg fra `blog-posts/`-mappen.

## 5 · Produkter
**Products → Add product**

Opret hvert produkt fra `products/`-mappen som dummy. Når rigtige produkter kommer, slet eller skjul disse.

## 6 · Navigation menus
**Online Store → Navigation**

Opret følgende menus (handles skal matche, ellers virker temaet ikke):

### `main-menu` (eksisterer allerede — bare opdater)
Brugt i header.
- Shop → `/collections/all`
- Nyheder → `/collections/nyheder`
- Bestsellers → `/collections/bestsellers`
- Om MAREA → `/pages/om-marea`
- Journal → `/blogs/journal`

### `footer-shop`
- Alle smykker → `/collections/all`
- Nyheder → `/collections/nyheder`
- Bestsellers → `/collections/bestsellers`
- SS26 Launch → `/collections/ss26-launch`

### `footer-service`
- Levering & retur → `/pages/levering-og-retur`
- FAQ → `/pages/faq`
- Kontakt → `/pages/kontakt`
- Handelsbetingelser → `/policies/terms-of-service`
- Privatlivspolitik → `/policies/privacy-policy`
- Cookiepolitik → `/pages/cookiepolitik`

### `footer-about`
- Om MAREA → `/pages/om-marea`
- Journal → `/blogs/journal`
- Bæredygtighed → `/pages/baeredygtighed`
- Pleje af smykker → `/pages/pleje`

## 7 · Policies (legal pages)
**Settings → Policies**

Disse 4 sider skal udfyldes (Shopify kobler dem automatisk til checkout):
- Refund policy → indhold fra `pages/refund-policy.md`
- Privacy policy → indhold fra `pages/privatlivspolitik.md`
- Terms of service → indhold fra `pages/handelsbetingelser.md`
- Shipping policy → indhold fra `pages/levering-og-retur.md`

## 8 · Theme settings (efter login)
**Online Store → Themes → Customize**

Verificér at:
- Logo er uploaded (Settings → Brand assets → upload `_brand/logo/MAREA_website_logo.png`)
- Farver matcher MAREA-paletten (Theme settings → Colors)
- Fonte er Cormorant Garamond + Inter (Theme settings → Typography)

## 9 · Apps (anbefalede)
- **Shopify Email** (gratis, til newsletters)
- **Shopify Inbox** (chat support)
- **Judge.me / Loox** (anmeldelser — senere)

## 10 · Når I er klar til launch
- I `templates/`: omdøb `index.launch.json` → `index.json` (overskriv eksisterende Coming Soon)
- Slet password protection: Online Store → Preferences → Password protection → uncheck
- Skift announcement bar tekst i header-group.json (eller i theme editor)
- Opdater eventuelle countdown timers
- Push til main-branchen → Shopify synker automatisk
