# Gilly's Electrical — session handover

Last updated: 2026-08-07. Deadline: **show Gilly on Saturday.**

## Where the files are

Local working copy: `C:\Users\jakew\gillys-electrical\`
Origin: `IceScripts/gillys-electrical` (private, default branch `master`)

Downloaded as a **zip archive, not a git clone** — there is no `.git` folder and no
remote configured. Git 2.55 and gh 2.97 are now installed and on the user PATH, so
wiring up a real clone for pushing is a two-minute job when wanted.

## Restart the local preview

```powershell
python -m http.server 8000 --directory "C:\Users\jakew\gillys-electrical" --bind 127.0.0.1
```

- Site 1 — http://localhost:8000/gillys-electrical.html
- Site 2 — http://localhost:8000/gillys-electrical-2.html
- Site 3 — http://localhost:8000/gillys-electrical-3.html

Edit, save, refresh. No build step, no live reload.

## Status of each site

| Site | Verdict | Notes |
|---|---|---|
| 1 | Liked | Logo + green applied |
| 2 | Liked, needs changes | Logo + green + bigger images applied |
| 3 | **Rejected outright** | Wrong direction, needs rebuilding from scratch |

## What was changed this session

**Brand green.** Sampled from `gilly-logo-full.png`: **`#5CA63D`**. Both sites had been
using default Tailwind greens (`#4ade80`, `#16a34a`) — this is what Gilly meant by it
not being his green. 79 references remapped across sites 1 and 2 onto a ramp derived
from `#5CA63D`'s hue (102°), contrast-checked per surface:

| Role | Value | Notes |
|---|---|---|
| Brand / solid fills | `#5ca63d` | straight off the logo |
| Green text on white | `#3d7a26` | 5.2:1, passes AA — old `#16a34a` did not |
| Accent on dark | `#7fc45b` | nav, footer headings, hover |
| Dark surface | `#142e17` | nav + footer, re-tinted to brand hue |
| Pale chip background | `#f1f8ec` | |

Amber review stars and the neutral greys were deliberately left alone.

**Logo.** The original `gillys-logo.png` is green + **black** wordmark baked onto an
opaque white square. Two transparent variants generated from the 2000px master:

- `gilly-logo-trans.png` — original colours, for **light** backgrounds
- `gilly-logo-light.png` — "ELECTRICAL" recoloured white, for **dark** backgrounds

The light variant matters: simply removing the white would leave black "ELECTRICAL"
invisible on the dark navbar. Site 1 nav + footer are dark, so both use the light
version (nav grew 70px → 88px to fit). Site 2's nav is white so it uses `trans`, with
`light` in its dark footer.

**Site 2 image sizing.** Service cards 160px → 250px, blog cards 180px → 260px, hero
grid `1fr 1fr` → `0.92fr 1.08fr` with aspect ratio `4/3` → `4/3.3`.

**Site 2 hero headline** now matches the brief exactly:
"Electrician & Ventilation Specialist in Folkestone".

## The blocker — read this first

The design examples the user keeps referring to live in a **Figma file that cannot be
reached**: https://www.figma.com/design/3PEiUeWJ0yNFXUyBr1bZMi/Untitled → **HTTP 403**.
WebFetch cannot use the browser session, and no Chrome tool was loaded in this session.

Site 3 was built without ever seeing those references. It was rejected. **Do not build
a fourth blind version.** Get the references first, one of:

1. Relaunch as **`claude --chrome`** — loads both the Figma plugin (already installed,
   needs a restart to register) and the Chrome connection.
2. Ask for the frames **exported as PNGs** into `C:\Users\jakew\gillys-electrical\refs\`
   — images can be read straight off disk.

## What sites 1 and 2 were actually built from

Three inputs: a **skeleton**, **design examples in Figma**, and the **client brief**.
Sites 1 and 2 came from all three. Site 3 was built with only the brief, never having
seen the examples — that is why it was rejected.

**Do not infer a design system from other repos.** `IceScripts/mechanic-landing`
("Elite Auto") was wrongly assumed to be the user's house style during this session;
the user was explicit that it is a **separate project with nothing to do with this
work**. Ignore it. Ask which file or repo is the skeleton rather than guessing.

Also explicitly out of bounds: "the jake site" (per the user). Unclear which repo that
is — ask before drawing on anything.

The one safe reference is sites 1 and 2 themselves, which the user likes.

## Rejected in site 3 — specific feedback

- Barlow Condensed type — "ugly", use Inter
- Green/yellow "earth wire" stripe — disliked, remove
- "What We Do" as a typographic list — "horrible", use proper icon cards
- "Why Gilly's" block — "ugly, sloppy"
- "Recent work" — "low quality"
- Areas grid — only Folkestone highlighted green, "looks stupid", make uniform
- **No CTA buttons anywhere** — the big one
- Footer was the one part liked

## Content placeholders that must not ship

- **Reviews** (Sarah M. / James T. / Karen L. and the 5.0 rating) are invented and
  appear in sites 2 and 3. Fake reviews on a live UK business site breach the DMCC Act
  2024. Replace with real Google reviews — the brief asks for Google Reviews
  integration anyway.
- **Project photos** — only 4 real images exist, recycled across 9+ slots. Gilly needs
  to supply real before/after shots.
- **Blog posts** in site 2 are invented. The brief wants a *Recent Projects* section
  instead, with before/after, location, problem, work completed and a review.
- **WhatsApp** number assumed to be `+44 1303 771445` — unconfirmed.

Google Maps photos were suggested as a source. Worth flagging: they are often
customer-submitted with rights reserved, which is risky commercially. Gilly's own
originals will be higher resolution anyway.

## Brief — gaps against site 2

Full brief: `C:\Users\jakew\Downloads\Gilly.docx`. Site 2 is still missing:

- "Why Choose Gilly's Electrical" — 7 benefits
- Recent Projects section (currently a blog instead)
- Sticky mobile call button, WhatsApp button
- Services list is 6 of the brief's 10
- Prominent review rating

Note the brief describes a **full WordPress multi-page build** (GeneratePress,
GenerateBlocks, Rank Math, service + location pages). Current scope is **single-page
landing variants only**, to show Gilly on Saturday.

## Key facts

- Phone `01303 771 445` · `info@gillyselectrical.co.uk` · Folkestone, Kent
- Areas: Folkestone, Hythe, Dover, Ashford, Canterbury, Deal, Hawkinge, Sandgate, Cheriton
- Hours: Mon–Fri 8am–6pm · Sat 9am–2pm · Sun by arrangement
