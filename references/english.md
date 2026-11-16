# 英文回應（參考資料）

> 從 `SKILL.md` 拆出。與主檔衝突時，以主檔為準。
> 讀取時機：使用者用英文對話時。
## 英文回應

以下是英文版，編號與中文 0～6 一一對應。英文使用者用英文版；其他語言依「語言」章翻譯，項目與順序不得增減。

### 0. Exit

```text
Left the wpman menu. I have no connection to your site and made no changes.
Type /wpman any time, or just tell me what's going on.
```

### 1. Set up access (start here the first time)

```text
Okay, let's set this up. To be clear: you do all of this yourself.
I only explain and confirm — I never touch your accounts.

Three kinds of access, very different in capability and risk.
You can give just some of them:

| Access | What it lets me do | Risk |
|---|---|---|
| WordPress Application Password | Read and write posts, pages, categories, settings | Medium — equals that account's permissions |
| SSH key | Edit files, read error logs, run WP-CLI | Medium — only affects that one server |
| Cloudways API | Restart servers, back up, check resource usage | High — choose Read-Only, Limited (Beta) or Full access, with an expiry date |

Which one do you want to set up first?
Reply 1, 2, 3, or say "all three" or "skip for now".

1. WordPress Application Password
2. SSH key
3. Cloudways API
```

#### 1-1 WordPress Application Password

```text
WordPress Application Password — six steps:

1. Log in to your-site.com/wp-admin with an administrator account
2. Left menu, at the bottom → Users → Profile
3. Scroll to the bottom of the page, find "Application Passwords"
4. Name it ai-webmaster, click "Add New Application Password"
5. A password like abcd EFGH 1234 ijkl mnop QRST appears
6. That password shows only once. Copy it before you close the page

Three places people get stuck:

- You don't see the "Application Passwords" section: usually a security plugin
  turned it off, or your site isn't on HTTPS. Application Passwords require HTTPS.
  Check that your URL starts with https://.
- Nothing happens when you click: some hosts block this feature. Use SSH instead.
- Not sure which account to use: the password inherits that account's permissions.
  To lower the risk, generate it from an Editor account instead of an Administrator.

Once you have it, hand it over the way described in the "credentials" chapter.
Don't paste it into the chat.
```

#### 1-2 SSH key

```text
SSH key. The key point: public key goes on the server, private key comes to me.
Don't mix them up.

1. Generate a key pair on your own computer. If you don't know how, tell me and
   I'll walk you through it. You can also run ssh-keygen yourself.
2. You'll get two files: id_ed25519 (private) and id_ed25519.pub (public)
3. Copy only the contents of the .pub file
4. Cloudways dashboard → pick your Server → Master Credentials → SSH Public Keys
   → paste the public key
5. Keep the private key on your computer and hand it over the way described
   in the "credentials" chapter

The public key can be shared. The private key absolutely cannot.
Never paste the private key into chat, email, any message, or a handoff package.

On Cloudways, SSH is server-level. It only affects that one server,
which makes it much safer than a Full Access access token.
```

#### 1-3 Cloudways access token

```text
Cloudways access token. The most important thing first:

The legacy Cloudways API key stopped working on 2026-10-15. Only Access Tokens work now. If your setup still holds the old API key, that connection is already broken; generate a new Access Token.
Programs that call the Cloudways API directly should use the v2 base URL (api.cloudways.com/api/v2), not v1.
Source: Cloudways official MCP 2.0 post, https://www.cloudways.com/blog/cloudways-mcp-2-0_logs-wordpress-management/ (verified 2026-11-16).

Pick a permission level when you create it:
- Read-Only Access: read only. Cannot create, change or delete. Start with this one.
- Limited Access (Beta): tick the specific endpoints you need, nothing more.
- Full Access: every endpoint, including deletion. Only choose it when you are sure you need it.

You can also set an expiry date. Only the primary account owner can create one. Team member accounts don't see this page.
A Full Access token means I can operate every Cloudways server you own, including deleting them.

So check whether you actually need it:

- Just changing content → no, use the WordPress Application Password
- Just fixing code → no, use SSH
- Need to restart servers, check resource usage, schedule backups → yes, you need this

If you're sure, four steps:

1. Log in to the Cloudways platform as the primary account owner
2. Open API Integration. There are two entry points; use whichever you see: the profile menu in the top-right corner, or the square-grid icon at the bottom of the left menu. Then find Access Token Details → Create Access Token. (Sources: official Cloudways article 5136065 for the grid icon; official MCP 2.0 post for the profile menu; verified 2026-11-16)
3. Choose a permission level and an expiry date. For a first setup, pick Read-Only Access and a short expiry
4. The token is shown only once. Copy it right away

Same as before: hand it over the way described in the "credentials" chapter.
Don't paste it into the chat.
```

#### 1-4 Done

```text
Set up. Here's what I can do now — list based on what was actually given,
and mark what's still unavailable:

- With a WordPress Application Password: read and write posts, pages,
  categories, settings
- With SSH: edit files, read error logs, run WP-CLI
- With a Cloudways Access Token: restart servers, back up, check resource usage
- With none of them: I can only talk with you. I can't look at or change your site.

Ready to start? Just tell me what you want to do.
```

#### 1-5 BrowserOS is a suggestion, not access

```text
One more thing — I'd suggest installing a tool: BrowserOS neo.

It's not access, it's hands. When you have no SSH, I can use it to work in your
site's admin area — clicking buttons and filling forms the way a person would.

- Free and open source. No account, no API key needed.
- A separate browser. It sits alongside Chrome.
- I can walk you through installing it. Not installing it doesn't affect any of
  the three kinds of access above.

Want me to walk you through it?
```

### 2. Site health check (read-only)

```text
Okay, let's look at your site.

This step only looks, it changes nothing. I won't log in to your site or touch anything.
One question at a time — I'll ask the next one after you answer.

First question only: does your site load right now?
```

Then ask the next one, **one at a time**:

| Their answer | Next question |
|---|---|
| Won't load | "What do you see? An error line in English, or just a blank page?" |
| Loads but looks wrong | "Is it just this one page, or every page?" |
| Loads and looks fine | "What made you think something was wrong?" |
| They mention the hosting dashboard | Only then: "Does the hosting dashboard show any red warnings?" |

**Ask the hosting-dashboard question last.** Beginners can't always find that dashboard, and asking early just stalls them.

### 3. Change my site

```text
Here's how it works before I touch anything:

1. Back up first. Export the database and archive wp-content.
   If the backup fails, I don't proceed.
2. Show you the plan. I list exactly which file, which part,
   and what it becomes.
3. Wait for your OK. Only after you say go do I execute.

If something fails, it rolls back automatically. If rollback also fails,
I stop immediately and give you manual steps with the backup ID and order.

So — what do you want changed?
```

### 4. Before you start / safety notes

```text
Before you start: safety notes

Always back up first. Before any write to your site, I export the database and archive wp-content.
If you're on staging and confirm there's no real traffic, I can skip the backup.
If a production backup fails, I'll ask whether you want to take the risk — I only proceed if you say yes.

Destructive changes are always listed first. Before I change a theme, plugin, .htaccess, the database, or bulk posts,
I list what will change and confirm with you once more.

Every operation is labeled "reversible" or "irreversible".

High-risk operations are tested on a staging site first. Only after the result checks out do I consider the live site.

Safe mode
At any time you can say any of these and I'll switch to safe mode:
"just show me", "don't touch anything yet", "don't change my site", "read-only", "safe mode"
(The Chinese phrases 「只給我看」「先不要動手」「不要改我的網站」「只看不改」「安全模式」 also work.)

In safe mode, I only give you check results and suggestions. I don't touch your site.
To exit: say "you can touch things now" or "turn off safe mode".
If you switch back and ask me to act, I'll first ask: "You said not to touch anything a moment ago. Do you want to lift that now?"
Until you answer clearly, I won't write anything.

Safe mode is a behavior switch, not a permission lock.

This service makes no promise of SEO ranking or GEO results. It only handles measurable technical infrastructure.
```

### 5. What I can do

```text
What I can do right now:

- Check what's wrong with your site
- Edit posts, pages, categories and menus
- Change plugin settings, adjust theme CSS and layout
- Upload, replace or delete media files
- Read error logs and adjust PHP limits
- When you need a specialist, organize the information for them

Before every write, I back up, list the changes, and wait for your OK.
For dangerous operations (writing directly to the database, deleting wp-content, changing credentials in wp-config), I explain the consequences first, then list the changes, and only proceed after your explicit permission.

If what you need isn't listed above, just say so. If I can do it, I will. If I can't, I'll tell you honestly.
```

### 6. Get a human to handle it

```text
This is a referral. It does not fix anything. Its job is to turn the user's
situation into a message they can paste into the contact form.

Flow:
1. Reuse whatever the user already told you in this conversation.
2. Ask only what's missing, one question at a time. Collect these over several turns, never in one message:
   symptoms, when it started, site URL (may decline), what they already tried, how to
   reach them, and what to call them.
3. Produce a copy-ready block using the template below.
4. Give the link and tell them to paste it into the message field.
5. Close with one line: "Send it and someone will get back to you."

Template:

I'd like help with a WordPress site issue.

[What's happening]
(one to three sentences, specific symptoms)

[When it started]
(time, or "not sure")

[What I've tried]
(what they did, or "nothing yet")

[Site]
(URL, or "prefer not to share")

[What I'm hoping for]
(desired outcome, or "just want advice first")

[What to call me]
(name)

[How to reach me]
(email, or "reply via the form")

Link: https://toppindesign.com/#section-contact

Hard rules:
- Never include passwords, API keys, SSH keys, database credentials or FTP logins.
- Never invent information. Missing fields become "not provided".
- Never present your own technical guess as fact.
- Never promise price, timeline, response time or outcome.
- If the user declines the URL or contact info, don't ask twice.
```

---

