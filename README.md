# Lea Meadows website

A simple, fast, static website for Lea Meadows — *The Smaller Proofs Collection*.
No build step, no plugins, nothing to keep updated. Just HTML and one stylesheet.

## What's here

| File | What it is |
|------|------------|
| `index.html` | Home page + main newsletter signup |
| `by-smaller-proofs.html` | Book 1 page + opening chapters |
| `a-proper-bloom.html` | Book 2 page + Chapter One |
| `a-proper-choice.html` | Book 3 page + Chapter One |
| `about.html` | About Lea + headshot |
| `404.html` | Friendly not-found page (Cloudflare serves it automatically) |
| `favicon.*`, `apple-touch-icon.png` | Site icon (rose sprig) — linked from every page |
| `css/style.css` | All colours, fonts, and layout (edit once, every page updates) |
| `images/` | Drop covers + headshot here (see `images/README.txt`) |

Every page has a Kit newsletter signup, and the footer links to your list too.

---

## Part 1 — Put it online (one-time setup, ~15 minutes)

You'll connect a GitHub copy of this folder to **Cloudflare Pages**. After this,
any edit you make on GitHub goes live by itself in about a minute.

### Step 1 — Create a free GitHub account & repository
1. Sign up / log in at <https://github.com>.
2. Click **New repository**. Name it e.g. `leameadows-site`. Keep it **Public**
   (or Private — both work). Click **Create repository**.
3. On the new repo page, click **uploading an existing file**.
4. Drag in **everything inside this `leameadows-site` folder** — the `.html`
   files, the `css` folder, and the `images` folder. Click **Commit changes**.

### Step 2 — Connect Cloudflare Pages
1. In the Cloudflare dashboard, go to **Workers & Pages → Create → Pages →
   Connect to Git**.
2. Authorize GitHub and pick your `leameadows-site` repo.
3. Build settings: leave **Framework preset = None**, and leave the build
   command and output directory **blank** (this is a plain static site).
4. Click **Save and Deploy**. In ~1 minute you'll get a live `*.pages.dev` URL.

### Step 3 — Point your domain at it
1. In your Pages project, open **Custom domains → Set up a custom domain**.
2. Enter `leameadows.com` (and add `www.leameadows.com` too if you like).
   Because your domain is already on Cloudflare, it wires up automatically.

Done. The site is live.

---

## Part 2 — Editing it yourself (the part you wanted)

You never need to touch Cloudflare again. To change anything:

1. On GitHub, open the file you want (e.g. `by-smaller-proofs.html`).
2. Click the **pencil ✏️ icon** (top right of the file) to edit.
3. Make your change, scroll down, click **Commit changes**.
4. Cloudflare redeploys automatically — live in about a minute.

Made a mistake? GitHub keeps every version. Click the file's **History** to see
past versions, or in Cloudflare Pages → **Deployments**, roll back to a previous
one with one click.

### Common edits — exactly where to make them

**Add the opening chapters**
Open a book's `.html` file and find the section that says
`Read the opening / The first four chapters`. Under each
`<h2>Chapter One</h2>`, replace the placeholder line with your text — one
paragraph wrapped in `<p>` ... `</p>` per paragraph. The fancy drop-cap and
chapter spacing happen automatically. (Tip: if you'd rather not format it by
hand, send me the chapters and I'll drop them in.)

**Turn a pre-order button into a buy button on launch day**
Each book page has a `buy-row` near the top and a matching button in the
end-of-sample "keep reading" block at the bottom — change both, plus the card
on `index.html`. Three things to update per book on launch day:
- `<p class="pub-status">Coming [date]</p>` → `Available now`
- the `Out [date]` line in the keep-reading block → `Out now`
- button text `Pre-order on Amazon` → `Read on Amazon` (link stays the same)

**Current links**
| Book | Status | Link |
|------|--------|------|
| By Smaller Proofs | Out now, wide | <https://books2read.com/by-smaller-proofs> |
| A Proper Bloom | 18 Aug 2026, KU (Amazon only) | <https://amzn.to/4ga4e5H> |
| A Proper Choice | 24 Aug 2026, KU (Amazon only) | <https://amzn.to/4g9xhot> |

Books 2 and 3 are in Kindle Unlimited, so they get one Amazon button only —
no other retailers until they leave KU.

**Add a cover or your headshot**
Put the image in the `images` folder using the exact name listed in
`images/README.txt` (e.g. `by-smaller-proofs.jpg`, `lea-meadows.jpg`).
Commit it — the placeholder is replaced by your image automatically.

**Change a colour or font**
Everything visual lives at the top of `css/style.css` under `:root`. Change a
hex code there and it updates across the whole site.

**Newsletter signup**
Every page has a custom-styled form that posts directly into your Kit account
(form **9603791**). It looks like the rest of the site but the email, the
confirmation message, and any Kit automations are all handled by Kit. To change
the wording on the button, edit the text inside `<span>Receive Lea's letters</span>`.
If you ever rebuild the form in Kit and get a new one, search the files for
`9603791` and `089a5491f1` and replace them with the new form's values (from
Kit's HTML embed).

---

## Notes
- The site reads as fan fiction inspired by Austen; the footer states this.
- Book 1 (*By Smaller Proofs*) can stay free; per your funnel plan, keep Books 2
  & 3 to sample chapters only here, since they're going into Kindle Unlimited.

### Bonus-scene pages (not in the site navigation)

`courage/`, `gravel/`, `wedding/`, and `wedding-epilogue/` are standalone bonus
scenes with their own PDFs. Nothing on the site links to them — they're meant to
be handed out by newsletter link. `wedding-epilogue/` is set to `noindex`;
`courage/` and `gravel/` are not, so search engines can find those two.

### The site icon

The little rose sprig in the browser tab is `favicon.svg` (plus `.ico` and PNG
fallbacks) in the top folder. To change it, replace those files keeping the same
names — the `<link rel="icon">` tags in each page's `<head>` point at them by
name and don't need editing. `images/icon-512.png` is a large copy kept for
social profiles or a press kit.
