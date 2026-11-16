<div align="center">

<img src="icon.png" width="128" alt="WordPress AI Webmaster">

# WordPress AI Webmaster

**Give your WordPress an AI brain.**

Connect it to the AI you already use, and call it from your desktop or your phone.
Ask it to change things, build things, or report a problem it just found.

It's like having a webmaster and an engineer on call, sharing the load.

[![License: MIT](https://img.shields.io/badge/License-MIT-c4a674.svg)](LICENSE)
[![Free](https://img.shields.io/badge/Free-open_source-171717.svg)](#-this-skill-is-completely-free)
[![WordPress](https://img.shields.io/badge/WordPress-6.0%2B-21759b.svg)](#-requirements)

**Language:** English · [繁體中文](README.md)

</div>

<br>

---

<br>

## 💰 This skill is completely free

No account, no payment, no credit card, no email.

You install this skill into the AI you already use. It runs on your own quota.

If you want more help, we offer separate WordPress services — none of which affect your use of this skill.
You're also welcome to join our Discord and talk shop with other WordPress site owners.

**Free forever. Full source code, in the open.**

<br>

---

<br>

## 🚀 How to use

<div align="center">

Once installed, type this in your AI chat

# `/wpman` ＋ your question

**That's it.**

</div>

Don't want to remember a command? Just talk:

> "My site seems broken. What do I do?"

Same result. It will ask you what to check next.

<br>

---

<br>

## ✨ What it can do for you

### 🗣️ Treat it like a real employee

> [!TIP]
> **Shift how you think about it:** you don't need to learn prompt syntax. **Treat it like a real employee sitting next to you.**  
> When something's wrong, don't try to work out "how should I instruct it" — just say it the way you'd normally say it. The right column is copy-paste ready:

| The problem | What you say, like handing work to a colleague |
|:---|:---|
| 🚨 **The site is broken** and you don't know where to start | **"My site seems broken. What do I do?"** |
| 🎨 **The design feels flat** and you want it to look professional | **"Redo the visual design — you can use your design skill"** |
| 🖼️ **You want a layout change** but don't dare touch it | **"Change the homepage carousel to three slides"** |
| 🔒 **You suspect a hack** and don't know how to check | **"Check whether the site has been hacked"** |
| ⚡ **The site got slow** and you can't find why | **"The site got slow. Take a look."** |
| 📝 **Titles are too long** and fixing them one by one is tedious | **"These three post titles are too long. Shorten them."** |
| 🛒 **You want a new feature** and don't know where to begin | **"I want to add a product category. How?"** |
| 🛡️ **You're afraid it will mess with your site** | **"Just show me. Don't change anything."** |

**When you call it, it opens with one line in character:**

> **"I'm your WordPress webmaster. Just tell me what you need."**

Then you say what you need. No menu numbers to pick.

> **You don't memorise commands or syntax. Think of something, say it the way you normally would.**
>
> If what you said isn't precise enough, it won't guess. It keeps asking until it genuinely understands the job,
> and only then does it start.

### 💡 An analogy

Your AI already has hands. It can type, click buttons, and run commands.

What this skill gives it is **a craftsman's judgement**:

> Whether this screw should be turned, how far, and how to fix it if you strip it.

The hands already worked. The difference is whether anyone told it when to stop.

### ✅ What it actually delivers

| It can | What that means in practice |
|---|---|
| **Understand plain speech** | Say it vaguely. It keeps asking until the job is clear — it won't guess its way into damage |
| **Explain before acting** | Before touching anything it says what it will change and what that affects. "Rename a title" and "drop the whole database" are entirely different jobs to it |
| **Clean up after itself** | It backs up before writing and rolls back on failure. If rollback also fails, it hands you manual steps |
| **Admit what it can't do** | If it can't, it says so. It won't pretend, and it won't act out a fix that never happened. If it truly can't solve it, it organises the information so you can take it to a human |
| **Understand "don't touch"** | Say "just show me" once and it won't touch your site for the rest of the session. And it speaks plain language to an owner, technical language to an engineer |

<br>

---

<br>

## 📋 Real examples

The three transcripts below are from actual runs, not mock-ups.

### Case 1 — A non-technical owner says "the site is broken"

> **You:** My site seems broken. What do I do?
>
> **Webmaster:** "Seems broken" covers a lot of ground. One question first: does your site load right now?
>
> **You:** It loads, but the page is blank white.
>
> **Webmaster:** A white screen usually means a plugin or theme broke. I can look into it and fix it — but I'll back up first, and show you exactly what I'm changing before I touch anything. Want me to start?
>
> **Want me to explain in more detail?**

**It didn't pretend to know. It didn't dump a wall of commands on you. And it asked one question, not five.**

---

### Case 2 — An engineer asks a technical question

> **You:** wp-admin returns 500. error_log shows `PHP Fatal error: Allowed memory size exhausted`
>
> **Webmaster:** That message means "out of memory", but there are two opposite causes, and the fixes are opposite:
> - Case A: the limit is set too low
> - Case B: something is consuming too much
>
> The byte count tells you which. 41943040 is 40M — WordPress's default per-page limit. 134217728 is 128M, which most plugins expect at minimum.
>
> **The last part matters.** The next thing to change is `WP_MAX_MEMORY_LIMIT` in wp-config.php.
> That constant **is not on the pre-approved list** — it needs a separate explicit setting and a second confirmation.
>
> **I won't change it on my own.**

**It knows where its authority ends, and says so out loud.**

---

### Case 3 — You want it to look before it touches

> **You:** Just show me, don't change anything. Is there a problem with my site?
>
> **Webmaster:** Read-only mode is on. **I won't touch anything.**
>
> You'll get a report: problem, impact, recommendation. Anything that requires action gets flagged separately,
> and **I only act once you say "go ahead"**.

<br>

---

<br>

## 🛡️ It does act — but it always stops and asks first

> [!IMPORTANT]
> **It will change your site. Before it does, three things always happen: back up, show you the list, wait for your OK.**  
> Sites break because things move too fast and leave no way back. So what we locked down is *the process*, not the ability to act.

### 🛑 Three gates — none can be skipped

1. 📦 **Back up first, then act.** Before any write, it exports the database and archives `wp-content`.
   Already on **staging** with no real traffic? Then no backup is needed.
   If a production backup fails, it won't decide for you — it asks: **"The backup failed. Do you want to take the risk and continue?"**
   You say yes, it proceeds. You say no, it stops.
2. 👀 **Show you first, then act.** Before acting it lists which file, which section, and what it becomes.
   "Optimise the SEO" is not an acceptable answer. Once you've read it and explicitly agreed, it acts.
3. 🔒 **Dangerous operations need two answers from you.** Direct database writes, deleting `wp-content`, changing credentials and keys in `wp-config`, resetting the database.

   **First question: do you want this at all?**

   It explains the consequences first — what the operation **does**, **the worst case**, whether it's recoverable, and whether there's a backup.
   You say "do it", and it moves on.

   **Second question: is this list correct?**

   It lists which file, which section, what it becomes. You read it, and if it's right,
   you reply "execute". Only then does it act.

   The two questions are different: the first asks *whether*, the second asks *whether it understood you*.
   If it got something wrong, that's your moment to stop it.

   "Yeah go ahead" or "whatever you think" doesn't count — it will ask again, "which item do you mean?"

   **There is no "always refused" — only "not allowed yet".**

### 📊 What it can do right now

| 🟢 Right now (through the three gates above) | 🔴 Needs one explicit permission from you |
|:---|:---|
| Edit post titles, content, categories, featured images | Write directly to the database |
| Change plugin settings, activate or deactivate a single plugin | Delete `wp-content` |
| Change theme CSS, layout, menu structure | Change database credentials or security keys in `wp-config` |
| Upload, replace, delete media files | Reset the database |
| Read error logs, adjust PHP limits | Delete a Cloudways server |
| Create pages, create categories, bulk-edit posts | |

> **The right column isn't "never" — it's "you haven't said yes yet".**
> It explains the consequences, then waits for one clear permission. Vague doesn't move it. Specific does.

> **It acts, but it never acts behind your back.**
> Say "just show me" at any time and it only inspects, touching nothing, until you say "go ahead".

### 🧯 If something breaks

Failure triggers automatic rollback. If rollback also fails, it stops immediately and leaves you manual steps —
with the backup ID and the restore order, so you can get back to where you started.

### 📋 What the menu looks like

Once installed, type `/wpman` (or `/站長` in Chinese) and you'll see:

```text
0. Exit
1. Set up access (start here the first time)
2. Site health check (read-only)
3. Change my site (backup first, show you, wait for your OK)
4. Before you start / safety notes
5. What I can do
6. Get a human to handle it

I'm your webmaster. Just tell me what you need.
```

**Nothing in that list is "coming soon".** Every item works today.

**Item 3 really does change your site.** But it backs up first, shows you the changes first, and waits for your OK.

**Item 6 is a referral.** It asks you a few questions, turns your answers into a block of text you can paste
straight into the contact form, and takes you there. You don't have to work out how to describe the problem,
and you don't have to prepare anything first.

That said, the menu is for people who don't know where to start. Most of the time you'll use the last line:
just say what you need. No numbers to remember.

<br>

---

<br>

## ⚠️ Safety requirements and disclaimer

> [!WARNING]
> **Important: once connected and authorised, this skill gives the AI deep access to your server and admin area.**  
> **Always run any operation in an environment with Staging or a current full Backup first.** Do not let an AI run write tests on a live production site without a backup.

### 👥 Use it according to your technical background

AI models differ enormously in reasoning ability. To protect your site, please use this skill according to your own capability:

| Background | Recommended use | Why |
|:---|:---|:---|
| 🟢 **Non-technical site owner / beginner** | **Read-only functions only — check, diagnose, consult** | AI agents vary in competence. If you don't know the underlying code, a hallucination or a misunderstanding can easily break files and destroy the site. **Once a problem is identified, hand the report to a professional engineer.** |
| 🔵 **Has WordPress expertise and understands the internals** | **Collaborative development, code changes, new features** | Even a capable AI still needs human judgement on WordPress hooks, plugin compatibility and database structure. You need the expertise to steer it around the traps. |

### 📜 Disclaimer

1. **Open source, as-is.** This project is a completely free open-source tool, provided **AS-IS**. The authors accept no legal or financial liability for any **white screen, corrupted code, data loss, SEO ranking change or business loss** arising from use of this skill, from an AI agent's misbehaviour, from a misunderstood instruction, or from model hallucination.
2. **Nothing malicious, guaranteed.** The source code and behaviour rules are fully public. **We will never build in sabotage or a back door.**
3. **Backups are your responsibility.** You are responsible for taking and keeping a complete backup (files and database) before any operation, so that you can restore to the original state 100% of the time if something goes wrong.
4. **Human experts available.** If a site does break, or you lack the ability to diagnose it, or you'd rather a professional team took over, we do offer paid [installation, recovery and ongoing maintenance](#-cant-install-it-or-want-more-paid-help-is-available).

<br>

---

<br>

## 🚨 Requirements (read before installing)

> [!WARNING]
> **Miss one and it's degraded.** Confirm the following before you start.

1. ☁️ **Cloudways recommended as host**  
   The four-layer cache flushing, server restarts, SSL and deep diagnostics are all built for **Cloudways**. Other hosts work, with limitations.  
   > 🎁 **Limited-time offer**: if you're going to use Cloudways, you're welcome to sign up through my referral link. **Both of us get US$50 (about NT$1,600) off**, which saves you hosting cost and is the most direct way to support the author:  
   > 👉 **[Claim the Cloudways US$50 referral discount](https://vrlps.co/iop6eoc/cp)**

2. 🤖 **Bring your own AI, and make it a capable one**  
   This tool is a behaviour spec — it installs into the AI you already use (Claude Code, Codex, Cursor, OpenCode, etc.). It runs on your own model quota or API key. We don't hold your account and never touch your data.

   **This isn't "any AI will do".**

   | | |
   |---|---|
   | ✅ **Use** | A frontier commercial model released in 2026 or later (the current flagship from a major vendor) |
   | ❌ **Don't use** | Very old models, free mini tiers, unknown small models |
   | ⚠️ **Not recommended** | Small local agents — context length and reasoning are usually insufficient |

   **Why does it matter?** This skill works because *the model can read the rules and is willing to follow them*.
   If the model isn't capable enough, the rules are just paper.

   The failure mode we see most: a weak model treats "rename a title" and "drop the whole database" as the same kind of task,
   and then does it. That's not the skill's fault. It's the model's.

   **But you don't need an AI that already knows WordPress.**

   This skill carries the WordPress judgement and the common traps — table prefixes, four-layer caching,
   serialised data, MU-plugins, the wp-config closed rule, Contact Form 7 field limits, and so on.
   It doesn't require your agent to be a WordPress expert. It just needs to be smart enough to follow the rules.

<br>

---

<br>

## 📦 Installing

Pick one of the three. They're ordered easiest first.

### Method 1 — Tell your AI to do it (easiest)

Paste this into your AI. It will work out where the files go:

```text
Install this skill for me: https://github.com/snowykenlai/wordpress-ai-webmaster
```

Restart your AI once afterwards and it's ready.

### Method 2 — One command

If you're comfortable with a terminal:

```bash
npx skills add https://github.com/snowykenlai/wordpress-ai-webmaster --global
```

This tool detects which AIs you have installed and puts the files in the right place.

### Method 3 — Manually

```bash
git clone https://github.com/snowykenlai/wordpress-ai-webmaster \
  ~/.claude/skills/wordpress-ai-webmaster
```

For Codex, use `~/.codex/skills/wordpress-ai-webmaster` instead, then restart.

> [!NOTE]
> **Install the whole folder, not just `SKILL.md`.** Since v2.0.0 the skill is split: `SKILL.md` plus a `references/`
> folder holding the English responses, the legal chapter, the WordPress chapter, and the host guides.
> If `references/` is missing, the skill still runs — it just has less detail to draw on.

### Starting it the first time

Restart your AI, then type `/wpman`. Or just say "something's wrong with my site".
`/站長` works too — both commands do the same thing.

<br>

---

<br>

## 🛠️ Can't install it? Or want more? Paid help is available

> [!NOTE]
> **Can't get it working?** If the steps don't make sense, or nothing happens after install, don't struggle alone.
>
> **Want to go further?** We're a professional studio, and we can also help with:
>
> - ⚡ Custom features for your WordPress site
> - 📚 Long-term maintenance, with someone to ask when you have questions
> - 👨‍💻 Optimising an existing site, or fixing problems that already showed up

| Service | What it covers |
|:---|:---|
| 🚀 **Installation** | Cloudways + WordPress + AI tooling, set up and working |
| 📦 **Migration** | Change host, change domain, move all files and the database intact |
| 🎓 **One-to-one coaching** | Running a site with AI, SEO / GEO in practice, WooCommerce |
| 🚑 **Rescue and repair** | Site down, hacked, white screen, locked out of admin — urgent diagnosis |
| 🛡️ **Monthly maintenance** | Scheduled backups, security monitoring, plugin updates, and general peace of mind |

**🚀 Get in touch — ToppinDesign**

📮 **Live chat**: https://toppindesign.com/#section-contact  
📧 **Email**: [service@toppindesign.com](mailto:service@toppindesign.com)  
🌐 **Services**: https://toppindesign.com/wordpress-expert/

> 💡 **To be clear**: this skill itself is **free forever and fully open source**. The above is our separate paid installation, coaching and monthly maintenance. If you can install it yourself, you don't need to spend anything. If you'd rather save the time, or you're stuck, you're welcome to get in touch.

## 🎁 Join our Discord: WordPress site owners talking shop

> [!TIP]
> Don't want to pay someone and would rather learn it yourself? There are people here doing the same.
>
> **WordPress site owners talking shop** is a community for WordPress site owners. Inside you'll find:
>
> - WordPress techniques that never made it into public posts, and how to dodge the plugin landmines
> - Real-world ways to run an AI webmaster — new features get tried here first
> - Stuck? Ask. Someone will answer.
>
> 👉 **[Join WordPress site owners talking shop](https://discord.gg/pending-invite)**
>
> (Invite link being set up — it will be updated here)

<br>

---

<br>

## 🔍 Under the hood

**You don't need any of this to use it. Read on only if you're curious.**

### ❓ What it actually is

Imagine hiring a webmaster.

He doesn't live at your house. There's no monthly salary, no desk to buy — because he lives inside the AI you already use.
Open your laptop or your phone, and he's there.

Say "something looks wrong with the site" and he knows where to look first. Say "change a title for me" and he asks
which post and what to. Say "just handle all of it" and he doesn't start immediately — he writes you a list and asks.

**That's the brain of that webmaster.**

It isn't a website. It isn't an app. There's no account to create. It's a very detailed set of instructions that writes down,
line by line, how a good webmaster works — then installs into the AI you already have
(Claude, Codex, Cursor and similar all work).

**It doesn't connect to your site on its own.**

To actually do anything it needs your AI and the access you grant. Its only job is one question:
should this be done, and how do you do it safely.

### 📌 Requirements

Confirm these before you go further.

| Item | Needed? | Notes |
|---|---|---|
| **WordPress site** | Required | 6.0 or later |
| **Cloudways hosting** | Recommended | Full functionality. Four-layer cache and server-level operations are built on Cloudways |
| **Other hosts** | Works, limited | cPanel, SiteGround, self-hosted: WordPress-level features work; cache and server-level features don't. It says so plainly |
| **An AI that supports skills** | Required | Claude Code, Codex, Cursor, OpenCode, etc. |
| **BrowserOS neo** | Optional | The hands when there's no SSH — operate the admin area through a browser. Free and open source |

> Other hosts work too. It won't help you less just because you're not on Cloudways — it will simply tell you
> which specific things it can't do, rather than pretending.

### 🚫 What it won't do

- It won't connect to your site on its own. That requires your AI and the tools you authorise
- It won't change anything before you agree
- It won't pretend a fix worked. If it can't, it says so
- It won't promise SEO rankings or AI-search visibility
- It won't ask for your password in the chat. Passwords only ever move between you and the browser

### 🔐 Safety design

#### 🧱 Seven-layer safety net

Every operation that writes to your site goes through these seven steps, in order, none skippable:

1. **Back up**: export the database, archive the files. If it fails, try the next approach; only after all four fail does it move to a risk statement
2. **Show you what will change**: list the exact changes. "Optimise the SEO" is not acceptable
3. **Confirm**: get your explicit agreement, matched to the risk level
4. **Reversibility label**: every item marked "reversible" or "irreversible"
5. **Test on staging**: high-risk operations are proven on staging first
6. **Write a log line**: one line per action, append-only
7. **Roll back automatically**: failure triggers rollback. If rollback fails, it stops at once and hands you manual steps

#### 🚦 Operation levels

| Level | Meaning | What it does |
|---|---|---|
| **G0 read-only** | Changes nothing | Acts immediately |
| **G1 reversible change** | Changes content, but recoverable | Proposes, then waits for your OK |
| **G2 high risk** | Files, plugins, themes | Explicit agreement + backup + proven on staging first |
| **G3 high risk** | Irreversible, or site-destroying | Explains the consequences, needs one clear permission from you, then lists the changes and acts |

**There is no "always refused". There is "not allowed yet".**

The specific G3 items — these need that explicit permission every time:

- Writing directly to the database
- Deleting `wp-content`
- Changing database credentials or security keys in `wp-config`
- Switching themes
- Deactivating every plugin
- Resetting the database
- Deleting a Cloudways server

**And wp-config.php has its own closed rule.**

Only four specific settings are allowed to change. Everything else is off limits. Get this file wrong and the whole site
goes white — you can't even reach the admin area.

#### 🔧 What happens if it breaks

It **backs up before acting**, and rolls back on failure.

If even the rollback fails, it stops immediately and leaves you manual restore steps —
the backup ID and the restore order — so you can get back to the original state.

### 🧩 What else needs installing

**One thing: BrowserOS neo.**

When there's no SSH, it's the webmaster's hands: the AI borrows the session you're already logged into in your browser
and operates the admin area directly, without ever touching your password.

BrowserOS neo is free, open source, needs no account and no API key. It's a separate browser that sits alongside Chrome,
and on first launch it can import your Chrome bookmarks and passwords in one click.

Download: https://www.browseros.com/download/

Launch it once after installing. It detects Claude Code, Codex or Cursor on your machine — one click to connect,
no config files to edit.

**Everything else is access, not installation:**

- WordPress access → generate an "Application Password" in the admin area
- Host access → provide an SSH key or a Cloudways Access Token

### 🎛️ How to control it

Normally you don't need to. It follows the rules above on its own. But if you want to step in, these four lines are fastest:

```text
"Just show me, don't change anything"   → read-only mode
"Go ahead"                              → lift it
"Back up before you do that"            → force a backup
"Show me the log"                       → see the operation log
```

These are switches, not incantations. Say them in your normal tone — it will understand.

### 🙋 FAQ

**Q: Is it free?**

Yes. Free forever, full source public. Read it, change it, fork it.

**Q: Do I need to know how to code?**

No. It assumes you're non-technical by default and explains in plain language with analogies. You can say
"explain in more detail" at any time to switch to technical mode.

**Q: Do I have to use Cloudways?**

No. But four-layer cache flushing and server-level operations (restart, SSL, backup restore) only work there.
On other hosts it will tell you exactly which items are unavailable.

**Q: Will it change my site on its own?**

No. Every write needs your agreement, and it lists the proposed changes first.

To be honest though: that's the *rules* constraining it. If your AI agent doesn't follow instructions, the rules are just paper.

So use a capable frontier model, not a free mini tier. The weaker the model, the more often it skips the rules.

**Q: What if it breaks something?**

The first of the seven layers is a backup, and failure rolls back automatically. You can also ask for
"back up before you do that" up front.

**Q: Which AIs are supported?**

Claude Code, Codex, Cursor, OpenCode, and any agent that supports the `SKILL.md` format.

**Q: How is this different from just asking an AI to change my site?**

A generic AI gives you commands, or just acts. This skill gives it **judgement**: what should be done,
what needs asking first, what must never be touched, and how to recover when something goes wrong.

**Q: Why "webmaster"?**

Because what it's imitating isn't a tool. It's a person who looks after your site.

<br>

---

<br>

> [!WARNING]
> 🚀 **Need professional WordPress maintenance? Get in touch — ToppinDesign.**
>
> 📮 **Live chat (bottom-right) / Book a time**: https://toppindesign.com/#section-contact

<br>

---

<br>

<div align="center">

**Completely free** · Fork it, use it, sell it

If this skill helped you, a ⭐ is the biggest thank-you.

**Language:** English · [繁體中文](README.md)

</div>
