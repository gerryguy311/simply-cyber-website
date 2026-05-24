# How to update simplycyber.io redirects

> Drop this file into the root of `steve-simplycyber/academy-website` (alongside `_redirects`) so it lives next to the thing it documents. Commit message: `docs: add REDIRECTS.md — how to update short links`.

---

simplycyber.io runs on Cloudflare Pages, served from the GitHub repo `steve-simplycyber/academy-website`. All the short-link redirects (like `simplycyber.io/discord`, `/threatlocker`, `/flare`, etc.) are controlled by **one file** in that repo called `_redirects`.

You edit that file → commit → push → it's live in ~30 seconds.

You can do the whole thing in the GitHub web UI in your browser — no terminal, no git commands needed. You can do it from your phone.

---

## The 30-second version

1. Go to: <https://github.com/steve-simplycyber/academy-website/edit/main/_redirects>
2. Find the line for the short link you want to change (or add a new line if it's a new short link)
3. Format is exactly three things separated by spaces:

   ```
   /shortlink   https://the-long-destination-url   302
   ```

4. Click the green **Commit changes…** button (top right)
5. Leave **Commit directly to main** selected → click **Commit changes**
6. Wait ~30 seconds, then test by going to `https://simplycyber.io/shortlink`

That's it. The Cloudflare build kicks off automatically the moment you commit. You can watch it on the Cloudflare dashboard if you want (Pages → academy-website → Deployments) but you don't have to.

---

## The format, explained line by line

Each redirect is one line. Three parts, separated by spaces:

```
/flare   https://flare.registration.goldcast.io/webinar/...   302
│        │                                                    │
│        │                                                    └─ 302 = temporary redirect (always use 302)
│        └─ The destination — the actual long URL you want people to land on
└─ The "short" part that comes after simplycyber.io/
```

So this line means: when someone visits `simplycyber.io/flare`, send them to that long Goldcast URL.

You can have as many lines as you want. Order doesn't matter. Lines starting with `#` are comments (notes for humans, ignored by Cloudflare).

---

## Today's change — a worked example

The old `/flare` line pointed at last month's webinar. I replaced it with the new one. The new line looks like this (all on **one line** in the file, even if it wraps on your screen):

```
/flare   https://flare.registration.goldcast.io/webinar/bf333deb-ad6e-42d9-84f8-a8a688670f8f?utm_campaign=43294564-WB%20-%20May2026%20-%20Training%20-%20Illicit%20Network%20Mapping%3A%20Using%20Data%20Pivots%20to%20Develop%20Illicit%20Connections%20-%20May%2028&utm_source=Influencers&utm_medium=Simply%20Cyber&utm_content=Livestream   302
```

That whole middle chunk is one URL — don't break the line. The `%20` stuff is just how spaces get encoded in URLs; leave it alone, copy the whole thing as-is from the sponsor.

Next time Flare gives you a new long link for a new webinar, you just edit that one line and replace the URL part.

---

## Common patterns

### Updating an existing short link (most common)

Find the line, change just the URL part, commit.

### Adding a new short link

Add a new line at the bottom. e.g. if a new sponsor sends you a long UTM link and you want `simplycyber.io/acme`:

```
/acme   https://acme.example.com/landing?utm_source=simplycyber&utm_medium=...   302
```

### Removing a short link

Delete the line, commit. `simplycyber.io/<that-link>` will 404.

### Temporarily disabling a link

Put a `#` at the start of the line to comment it out:

```
# /flare   https://old-url   302
```

---

## Things that will trip you up (so they don't)

1. **Three parts per line, separated by spaces.** If you accidentally put a tab or break the URL onto two lines, that redirect breaks. Stick to one line per redirect.

2. **Always 302, not 301.** 301 is "permanent" and browsers cache it forever — if you ever want to change that link again, people who visited the old one will still get sent there for months. 302 is safe; use it every time.

3. **The short part starts with a slash.** `/flare`, not `flare`.

4. **Copy the long URL exactly as the sponsor gave it to you** — including all the `%20` and `?` and `&` junk. Don't try to clean it up. That junk is the tracking the sponsor is paying for.

5. **Test in a private/incognito window.** Your normal browser may have the old redirect cached and confuse you into thinking the change didn't work. Incognito always hits fresh.

---

## If something goes wrong

- **Click the deployment in Cloudflare** (Pages → academy-website → Deployments) — if it shows a red ❌, click it to see the error message.
- **Worst case, revert your commit.** Go to the file's history on GitHub, find the previous good version, copy it back. Site is back to the old state in 30 seconds.
- **Or text me.** But you won't need to.

---

## Bookmarks worth saving

- Edit `_redirects` directly: <https://github.com/steve-simplycyber/academy-website/edit/main/_redirects>
- View current `_redirects`: <https://github.com/steve-simplycyber/academy-website/blob/main/_redirects>
- File history (for rollback): <https://github.com/steve-simplycyber/academy-website/commits/main/_redirects>
- Cloudflare deployments: <https://dash.cloudflare.com> → Pages → academy-website → Deployments

---

That's the whole game. Cloudflare + GitHub + one file. Faster than the Wix UI was, and you can do it from your phone if you have to.
