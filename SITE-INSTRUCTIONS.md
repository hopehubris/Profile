# Site Instructions
## ashisheth.com — Content & Maintenance Guide

---

## Site Structure

```
ashi-sheth.html          ← Main site (home, about, experience, advisory, contact)
writing.html             ← Writing index (list of all posts)
writing/
  _post-template.html    ← Blank template — copy this for every new post
  on-inheriting-broken-teams.html
  ai-automation-what-we-actually-built.html
  what-chros-actually-need.html
  [your-future-posts].html
```

All files are plain HTML. No build tools, no frameworks, no dependencies beyond a Google Fonts link. Open any file in a browser to preview it locally before publishing.

---

## How to Publish a New Post

### Step 1 — Copy the template

Duplicate `writing/_post-template.html` and rename it using your post's slug:

```
writing/your-post-title-in-lowercase-with-hyphens.html
```

**Slug rules:**
- Lowercase only
- Hyphens instead of spaces
- No special characters or punctuation
- Keep it short and descriptive

**Examples:**
```
writing/why-hr-tech-consolidations-fail.html
writing/what-pe-firms-get-wrong-about-it.html
writing/the-real-cost-of-a-bad-vendor-contract.html
```

---

### Step 2 — Fill in the post file

Open your new file and update every field marked with ✏️. Here's what each one is:

**In the `<head>`:**
```html
<title>YOUR POST TITLE HERE — Ashi Sheth</title>
<meta name="description" content="1–2 sentence summary for search engines and social previews." />
```

**In the post header:**
```html
<span class="post__date">June 2025</span>   ← Month + year

<span class="tag">Leadership</span>          ← Tags (see tag options below)

<h1 class="post__title">
  Your Post Title Here
</h1>

<p class="post__lede">
  The opening paragraph — 2–3 sentences that state the tension
  or situation the post explores. This is what draws people in.
</p>
```

**Available tags** (use 1–2 per post):
- `Leadership`
- `AI & Automation`
- `HR Tech`
- `Advisory`
- `Culture`

---

### Step 3 — Write the body

Inside `<div class="post__body">`, write your post using these elements:

| Element | Use for |
|---|---|
| `<p>` | Body paragraphs |
| `<h2>` | Section headings |
| `<h3>` | Label-style subheadings (smaller, uppercase) |
| `<blockquote>` | Pull quotes — a single strong sentence that deserves to stand alone |
| `<ul><li>` | Bullet lists (styled as em-dashes automatically) |
| `<strong>` | Bold — use sparingly, for key terms only |
| `<em>` | Italics — for asides or caveats |

**Examples:**

```html
<p>Your paragraph text goes here.</p>

<h2>A Section Heading</h2>

<h3>A label-style subheading</h3>

<blockquote>
  A single sentence that deserves to stand alone.
</blockquote>

<ul>
  <li>First point</li>
  <li>Second point</li>
  <li>Third point</li>
</ul>

<p>Text with a <strong>key term</strong> bolded and an <em>aside in italics</em>.</p>
```

**Optional: stat callout block**

For posts where you want to highlight numbers visually (like the AI automation post), add this block anywhere in the body:

```html
<div class="stat-row">
  <div class="stat-row__item">
    <div class="stat-row__num">90%</div>
    <div class="stat-row__label">Brief label describing the stat</div>
  </div>
  <div class="stat-row__item">
    <div class="stat-row__num">↓33%</div>
    <div class="stat-row__label">Brief label describing the stat</div>
  </div>
  <div class="stat-row__item">
    <div class="stat-row__num">$0</div>
    <div class="stat-row__label">Brief label describing the stat</div>
  </div>
</div>
```

Note: the stat-row CSS is only included in `ai-automation-what-we-actually-built.html` right now. To use it in other posts, copy the `.stat-row` CSS block from that file into your new post's `<style>` section.

---

### Step 4 — Add the post to writing.html

Open `writing.html` and find the comment that says:

```html
<!-- ─── ADD NEW POSTS ABOVE THIS LINE ─── -->
```

Add your post **above** that comment, at the top of the list (newest first):

```html
<a class="post-item reveal" href="writing/your-post-slug.html" data-tags="tag1 tag2">
  <span class="post-item__date">Month YYYY</span>
  <span class="post-item__title">Your Post Title Here</span>
  <span class="post-item__tags">
    <span class="tag">Tag One</span>
    <span class="tag">Tag Two</span>
  </span>
  <span class="post-item__arrow">↗</span>
</a>
```

**The `data-tags` attribute** controls filtering. Use the lowercase hyphenated versions of your tags, separated by spaces:

| Tag label | data-tags value |
|---|---|
| Leadership | `leadership` |
| AI & Automation | `ai-automation` |
| HR Tech | `hr-tech` |
| Advisory | `advisory` |
| Culture | `culture` |

Example for a post tagged Leadership and Culture:
```html
data-tags="leadership culture"
```

---

### Step 5 — Update the teaser on the main site (optional)

`ashi-sheth.html` shows a teaser of your 3 most recent posts. When you publish something new, update that section to keep it current.

Find the writing teaser section (search for `id="writing"`) and update the three `<a class="writing-teaser__item">` entries to reflect your latest posts. Keep it to exactly 3 — newest at the top.

```html
<a class="writing-teaser__item" href="writing/your-post-slug.html">
  <span class="writing-teaser__date">Month YYYY</span>
  <span class="writing-teaser__title">Your Post Title</span>
  <span class="writing-teaser__arrow">↗</span>
</a>
```

---

### Step 6 — Upload

Upload the changed files to your host. If you're using Netlify (recommended), drag the entire folder onto the Netlify dashboard. Only changed files need to be re-uploaded if you're using FTP.

**Files to upload after adding a new post:**
- `writing/your-new-post.html` (always)
- `writing.html` (always — the index changed)
- `ashi-sheth.html` (if you updated the teaser)

---

## How to Edit Existing Content

### Updating the main site (bio, experience, advisory services)

Open `ashi-sheth.html` in a text editor. The sections are clearly marked with HTML comments:

```
<!-- ─── About ─── -->
<!-- ─── Story / Experience ─── -->
<!-- ─── Offering ─── -->
<!-- ─── Writing teaser ─── -->
<!-- ─── Contact ─── -->
```

Find the section you want to edit and update the text between the HTML tags. Don't change the class names or structure — just the words.

### Updating contact details

In `ashi-sheth.html`, find the Contact section and update:
```html
<a class="contact__link" href="mailto:your@email.com">
<a class="contact__link" href="https://linkedin.com/in/yourhandle">
<a class="contact__link" href="tel:+11234567890">
```

The same links appear in the footer of every post file (`writing/*.html`). Update those too.

### Adding a new advisory service or experience role

**Advisory (Offering section):** Find the `<div class="offer">` block you want to model yours on and duplicate it. There are currently 3. Adding a 4th will break the 3-column grid — either replace one of the existing three or leave it at 3.

**Experience (Story section):** Each role is a `<div class="role">` block. Copy an existing one and update the dates, company, title, and description. Add new roles at the top of the list (most recent first).

---

## Adding a New Topic Filter

If you want to add a new filter category to the writing index (e.g. "Operations" or "Speaking"):

**In `writing.html`, add a new filter button:**
```html
<button class="filter-btn" data-filter="operations">Operations</button>
```

**Then use it on post items:**
```html
data-tags="operations"
```

**And add the matching tag label to posts:**
```html
<span class="tag">Operations</span>
```

No other code changes needed — the filter script handles the rest automatically.

---

## Design Rules

If you ever want to make visual changes, these are the core design tokens at the top of each file's `<style>` block. Changing them here changes the look sitewide for that file:

```css
:root {
  --bg:       #F7F6F3;   /* Page background — warm off-white */
  --ink:      #0E0E0E;   /* Primary text — near black */
  --muted:    #787570;   /* Secondary text, labels, dates */
  --rule:     #DEDAD4;   /* Lines, borders, dividers */
  --font:     'Zen Kaku Gothic New', sans-serif;
  --track:    0.12em;    /* Letter spacing — default */
  --track-lg: 0.18em;    /* Letter spacing — labels and nav */
  --rail-w:   1px;       /* Border weight throughout */
}
```

Keep changes minimal. The design works because of restraint.

---

## Checklist for Every New Post

Before you upload, run through this:

- [ ] File saved in `writing/` with a hyphenated lowercase slug
- [ ] `<title>` updated with the post title
- [ ] `<meta name="description">` filled in (1–2 sentences)
- [ ] Date, tags, title, and lede all updated
- [ ] Post body written and proofread
- [ ] New row added to `writing.html` (newest at top)
- [ ] `data-tags` attribute matches the filter categories
- [ ] Writing teaser on `ashi-sheth.html` updated if this is one of your 3 most recent
- [ ] All files uploaded to host

---

*Questions? Come back to this conversation and ask — the full site context is here.*
