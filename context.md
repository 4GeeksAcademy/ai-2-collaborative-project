# French Boutique Website Context

## 1. Project Mission
This document is the source of truth for a multi-page website for an old-fashioned French women's boutique.

This scope is strictly for a boutique storefront experience centered on products, catalog browsing, cart, and checkout.

Allowed technologies only:
- HTML
- CSS
- Tailwind CSS (CDN method only)

Global constraints:
- Mobile-first approach is mandatory.
- SEO and GEO best practices are mandatory.
- Semantic HTML is strictly enforced.
- JavaScript behavior is out of scope for this phase.
- Placeholder images must be clothing-focused.
- Tailwind must be loaded via CDN in each page `head` (no npm/build pipeline for this phase).

Tailwind setup (required on every page):

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Page Title | Maison Elise</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
```

Current page scope only:
1. Home page
2. Catalog
3. Product view
4. Cart
5. Checkout

## 2. Visual Direction
Brand mood:
- Elegant, classic, Parisian, and feminine.
- Editorial spacing and refined composition.
- Warm, soft neutrals with one deep luxury accent.

Copy tone:
- Sophisticated and clear.
- Short and descriptive.
- Focus on fit, material, and occasion.

## 3. Shared Design System

### 3.1 Color Tokens
Use these exact tokens in all branches.

```css
:root {
  --color-bg-main: #f7f2ea;
  --color-bg-soft: #fffaf3;
  --color-surface: #ffffff;
  --color-text-main: #1f1a17;
  --color-text-muted: #6f655d;
  --color-border-soft: #d8ccbc;
  --color-accent-primary: #6f2a2f;
  --color-accent-hover: #8a3a43;
  --color-ok: #596247;
  --color-note: #a36d2f;
}
```

Color usage rules:
- Backgrounds: `--color-bg-main`, `--color-bg-soft`
- Primary text: `--color-text-main`
- Secondary text: `--color-text-muted`
- CTA and key highlights: `--color-accent-primary`
- Dividers and subtle lines: `--color-border-soft`

### 3.2 Typography
Heading family:
- Cormorant Garamond, Times New Roman, serif

UI/body family:
- Source Sans 3, Helvetica Neue, Arial, sans-serif

Scale:
- H1: 2rem mobile, 3rem desktop
- H2: 1.5rem mobile, 2.25rem desktop
- H3: 1.25rem mobile, 1.5rem desktop
- Body: 1rem
- Meta text: 0.875rem

Rules:
- Exactly one H1 per page.
- Headings use serif.
- Navigation, labels, form fields, and metadata use sans-serif.

### 3.3 Spacing and Layout
Spacing scale:
- 4, 8, 12, 16, 24, 32, 48, 64

Radius:
- Inputs/cards: 8px
- Primary CTA optional pill: full rounded

Breakpoints:
- Base: 320+
- sm: 640+
- md: 768+
- lg: 1024+
- xl: 1280+

Container:
- Max width near 1200px with balanced lateral padding.

## 4. Strict Semantic HTML Enforcement
All page pull requests must satisfy semantic HTML requirements.

Required global page skeleton:
1. `header`
2. `nav`
3. `main`
4. `footer`

Required element usage:
- `section` for thematic blocks
- `article` for independent content units such as product cards or cart item entries
- `aside` for complementary blocks such as cart summary
- `figure` and `figcaption` for product imagery where caption adds context
- `form`, `fieldset`, `legend`, and `label` for checkout/form groups

Heading hierarchy rule:
- No skipped heading levels.

Accessibility baseline:
- Descriptive alt text for all product and hero images.
- Visible form labels.
- Visible keyboard focus states.
- Adequate contrast for text and controls.

## 5. Placeholder Image Policy
Use only fashion/clothing placeholders.

Approved categories:
- Dresses
- Blouses
- Pants
- Skirts
- Coats
- Shoes
- Accessories (bags, belts, scarves)

Aspect ratio standards:
- Product cards: 4:5
- Hero image: 16:9 or 21:9
- Cart thumbnails: 1:1

Naming pattern:
- placeholder-dress-01.jpg
- placeholder-blouse-02.jpg
- placeholder-heels-01.jpg

## 6. Reusable Global Components
Navbar and footer must remain visually and structurally consistent across all pages.

### 6.1 Navbar (Required on all pages)
Content:
- Brand mark/name
- Search field (visual only)
- User account entry (visual only)

Primary navigation policy:
- Top navbar links must include only: Home, Catalog, Cart.
- Product page access must come from selecting a product item in the Catalog listing.
- Checkout page access must come from the Cart summary action (purchase/continue flow).

Semantic structure:
- In `header`
- Main links in `nav` with a list structure

Responsive behavior:
- Mobile: top row brand + account, second row full-width search
- Desktop: one row with brand left, search center, account right

Canonical implementation (copy/paste on every page):

```html
<header class="border-b" style="border-color: var(--color-border-soft); background: var(--color-bg-soft);">
  <div class="mx-auto max-w-[1200px] px-4 py-3 sm:px-6 lg:px-8">
    <div class="flex items-center justify-between gap-3">
      <a href="index.html" class="font-serif text-2xl tracking-wide" style="color: var(--color-text-main);">Maison Elise</a>
      <a href="#" class="text-sm font-semibold uppercase tracking-[0.08em]" style="color: var(--color-text-main);">Account</a>
    </div>

    <nav aria-label="Primary" class="mt-3">
      <ul class="flex flex-wrap items-center gap-x-4 gap-y-2 text-sm">
        <li><a href="index.html" class="hover:underline">Home</a></li>
        <li><a href="catalog.html" class="hover:underline">Catalog</a></li>
        <li><a href="cart.html" class="hover:underline">Cart</a></li>
      </ul>
    </nav>

    <form role="search" aria-label="Site search" class="mt-3">
      <label for="site-search" class="sr-only">Search products</label>
      <input
        id="site-search"
        name="q"
        type="search"
        placeholder="Search dresses, blouses, coats..."
        class="w-full rounded-md border px-3 py-2 text-sm"
        style="border-color: var(--color-border-soft); background: var(--color-surface); color: var(--color-text-main);"
      />
    </form>
  </div>
</header>
```

Desktop enhancement classes (optional on container wrappers):
- Keep brand/account/search in a single row from `lg` and above.
- Preserve the same spacing, border, and typography tokens.

### 6.2 Footer (Required on all pages)
Content sections:
1. Categories: footwear, shirts, pants, accessories
2. Legal: terms and conditions, privacy policy, about the brand
3. Contact: boutique contact information

Note:
- This section provides the boutique's support/contact details only.

Responsive behavior:
- Mobile: stacked groups
- Desktop: 3-4 columns

Canonical implementation (copy/paste on every page):

```html
<footer class="mt-12 border-t" style="border-color: var(--color-border-soft); background: var(--color-bg-soft);">
  <div class="mx-auto grid max-w-[1200px] gap-8 px-4 py-10 sm:px-6 lg:grid-cols-3 lg:px-8">
    <section aria-labelledby="footer-categories">
      <h2 id="footer-categories" class="font-serif text-xl" style="color: var(--color-text-main);">Categories</h2>
      <ul class="mt-3 space-y-2 text-sm" style="color: var(--color-text-muted);">
        <li><a href="#" class="hover:underline">Footwear</a></li>
        <li><a href="#" class="hover:underline">Shirts</a></li>
        <li><a href="#" class="hover:underline">Pants</a></li>
        <li><a href="#" class="hover:underline">Accessories</a></li>
      </ul>
    </section>

    <section aria-labelledby="footer-legal">
      <h2 id="footer-legal" class="font-serif text-xl" style="color: var(--color-text-main);">Legal</h2>
      <ul class="mt-3 space-y-2 text-sm" style="color: var(--color-text-muted);">
        <li><a href="#" class="hover:underline">Terms and Conditions</a></li>
        <li><a href="#" class="hover:underline">Privacy Policy</a></li>
        <li><a href="#" class="hover:underline">About the Brand</a></li>
      </ul>
    </section>

    <section aria-labelledby="footer-contact">
      <h2 id="footer-contact" class="font-serif text-xl" style="color: var(--color-text-main);">Contact</h2>
      <address class="mt-3 not-italic text-sm leading-6" style="color: var(--color-text-muted);">
        Maison Elise Boutique<br />
        24 Rue des Rosiers, Paris<br />
        hello@maisonelise.fr<br />
        +33 1 44 00 12 34
      </address>
    </section>
  </div>
</footer>
```

Consistency rule:
- Contributors must reuse this footer structure and link grouping exactly.

## 7. Page-by-Page Requirements

### 7.1 Home
Required sections:
1. Shared navbar
2. Hero highlighting a campaign or featured products
3. Horizontal card list: New arrivals
4. Horizontal card list: Best sellers
5. Shared footer

Card anatomy:
- Clothing placeholder image
- Product name
- Price
- Optional short descriptor

Responsive behavior:
- Mobile: horizontal scrolling card rails
- Desktop: stable row layout with consistent card width

### 7.2 Catalog
Required sections:
1. Shared navbar
2. Filter bar before listing
3. Product listing grid
4. Shared footer

Navigation requirement:
- Each product card must provide an internal link to the Product View page.

Filters shown:
- Category
- Size

Grid target:
- Desktop reference: 4x5 (20 visible products)
- Mobile: 1-2 columns

### 7.3 Product View
Required sections:
1. Shared navbar
2. Main product block
3. Detail block
4. Shared footer

Main product block:
- Desktop two-column split
- Left column: primary product image (near half width)
- Right column includes:
  - Name
  - Code/reference
  - Size
  - Price
  - Quantity selector (visual only)
  - Add to cart button (visual only)

Detail block must include:
- Materials
- Recommended use scenarios

### 7.4 Cart
Required sections:
1. Shared navbar
2. Full page cart view
3. Product row list
4. Summary panel
5. Shared footer

Navigation requirement:
- The summary panel purchase action must provide an internal link to the Checkout page.

Cart row fields:
- Thumbnail
- Unit price
- Quantity
- Total per product

Summary fields:
- Subtotal
- Tax
- Total
- Purchase button (visual only)

Mandatory demo content:
- Exactly 3 sample products

### 7.5 Checkout
Required sections:
1. Shared navbar
2. Checkout header/progress
3. Three-step form content
4. Shared footer

Required flow:
1. Personal details
2. Shipping address
3. Card payment details

Form constraints:
- Semantic grouped form sections
- Clear labels and helper text
- No real payment processing logic

## 8. SEO Rules (Mandatory)
Per page:
- Unique title
- Unique meta description
- Exactly one H1
- Descriptive alt text
- Internal links to relevant pages
- Human-readable URL/file naming

Internal linking minimums:
- Catalog page includes links from product cards to Product View.
- Cart page includes a link from summary purchase action to Checkout.

Suggested title pattern:
- Home: Maison Elise | French Women Boutique
- Catalog: Catalog | Maison Elise
- Product: Product Details | Maison Elise
- Cart: Your Cart | Maison Elise
- Checkout: Checkout | Maison Elise

## 9. GEO Rules (Mandatory)
Goal:
- Make page content easy for AI answer systems to parse and summarize.

Rules:
- Keep product facts explicit and structured.
- Use stable entity naming for brand, product type, material, color, and size.
- Prefer concise paragraphs and bullet-point facts.
- Add short summary lines in major sections.

Markup-ready guidance for later stage:
- Organization
- Product
- BreadcrumbList
- FAQ (where needed)

## 10. Team Workflow for 5 Contributors
Recommended ownership:
1. Contributor A: Home page
2. Contributor B: Catalog page
3. Contributor C: Product View page
4. Contributor D: Cart page
5. Contributor E: Checkout page

Shared component rule with single-page ownership:
- Each collaborator owns one page, but all collaborators must copy the same canonical navbar and footer from Section 6 without structural changes.

Branch consistency rules:
- Do not redefine tokens per page.
- Reuse shared navbar/footer exactly.
- Keep top navbar links limited to Home, Catalog, and Cart across all pages.
- Verify mobile and desktop screenshots before PR.
- Run semantic HTML checklist before review.

Definition of done per page:
- Meets page block requirements.
- Uses shared color and typography tokens.
- Uses clothing placeholder imagery only.
- Passes semantic structure requirements.
- Passes SEO and GEO checklist.

## 11. Final QA Checklist
Before merge, verify:
1. Shared navbar/footer match the global spec.
2. Product is reachable from Catalog product cards, and Checkout is reachable from Cart summary action.
3. Mobile-first behavior is complete before desktop refinements.
4. Semantic landmarks and heading hierarchy are correct.
5. Placeholder images are clothing-focused and ratio-consistent.
6. All required page sections from the assignment are present.
7. SEO requirements are complete.
8. GEO requirements are complete.
9. The implementation remains aligned to boutique storefront scope only.

## 12. Out of Scope
- Authentication system
- Dynamic cart persistence
- Payment gateway integration
- Interactive filtering logic
- JavaScript-driven UI behavior

This context is active until assignment scope changes.
