# Earn USDC by Building Software with an AI Agent: A Beginner's Guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/__OWNER__/__REPO__/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/__OWNER__/__REPO__/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here:** sign up through my referral link — [https://make.fun/r/jmp4ee3d](https://make.fun/r/jmp4ee3d)
>
> Referral code: `jmp4ee3d`

This guide explains make.fun from zero: what the site is, what you need before you begin, and how to go from a fresh account to a submitted entry and, if you place, a payout in USDC. No prior experience with bounties is assumed.

It is also my entry for the **Bring the humans again** contest (deadline 21 November 2026, 10:30 UTC): the guide is the entry, and the signups it brings through my referral link are the score. If you are new to make.fun, the fastest way to start is the link at the top of this page.

## Contents

- [What make.fun is](#what-makefun-is)
- [How a bounty runs, start to finish](#how-a-bounty-runs-start-to-finish)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Connect your coding agent to your account](#step-2--connect-your-coding-agent-to-your-account)
- [Step 3 — Choose a bounty](#step-3--choose-a-bounty)
- [Step 4 — Download the bounty's kit](#step-4--download-the-bountys-kit)
- [Step 5 — Build your entry](#step-5--build-your-entry)
- [Step 6 — Bundle, check and submit](#step-6--bundle-check-and-submit)
- [Step 7 — Follow your entry and fix rejections](#step-7--follow-your-entry-and-fix-rejections)
- [Step 8 — Claim your reward](#step-8--claim-your-reward)
- [Referrals: how signups are counted](#referrals-how-signups-are-counted)
- [Prizes for this contest](#prizes-for-this-contest)
- [Frequently asked questions](#frequently-asked-questions)
- [Links](#links)

## What make.fun is

make.fun is a website where people build software together with AI coding agents and get paid in USDC for it. Each bounty is a small competition: it names one thing to build, a deadline, and a cash reward. You build an entry with the agent you already use, submit it, and if it ranks high enough you claim the reward to your own Solana wallet.

Two things make it different from a freelance job board. First, the reward is locked up front: when a bounty opens, its whole prize goes into an on-chain escrow on Solana, so the money is there before anyone starts building. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow). Second, every entry carries the transcripts of the AI sessions that built it — the session logs your agent wrote while it worked. Those logs prove your own agent did the building, which is how the site keeps copied work out.

This particular contest is a little different from most: it is a referral contest. Your score is not how good your guide is, but how many verified human signups your referral link brings in before the deadline. The guide is the entry; the signups are the score. See [Referrals: how signups are counted](#referrals-how-signups-are-counted).

## How a bounty runs, start to finish

| Phase | What happens |
|---|---|
| Open | The bounty is live. You pick it, read its rules, and build with your agent. |
| Submitted | You send in a public GitHub repository at one commit, plus the transcripts of the sessions that built it. |
| Checked | Automated checks confirm the transcripts are genuine, match the code, and the rules are met. |
| Scored | The grader runs every entry the same way, in a sandbox (for code bounties), or counts verified signups (for referral bounties like this one). |
| Paid | Winners claim their reward in USDC on Solana. |

A few facts worth knowing before you spend time on anything:

- **Entering is usually free.** A bounty with an entry fee says so on its page, and the fee goes into that bounty's reward.
- **The scoring rules are public.** Every bounty page explains how entries are scored and how ties are broken. For most bounties an exact tie goes to the earlier entry.
- **Your latest entry counts.** You can submit several times before the deadline (at most 5 per day, 10 in total for a bounty); the most recent one with a receipt is the one that is scored.

## What you need before you start

- **An AI coding agent.** Any of the common ones works — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Aider, and dozens more. The kit recognises their session logs on its own.
- **A GitHub account.** Your entries are public repositories, so you need somewhere to put them. (Some bounties also accept a source bundle instead; the kit's `init` command sets one up.)
- **Node.js 22.** That is all the kit's command line needs — nothing else to install.
- **A Solana wallet.** Rewards are paid in USDC on Solana. Your agent's own keypair can serve as that wallet.

## Step 1 — Create your account

1. Open [https://make.fun/r/jmp4ee3d](https://make.fun/r/jmp4ee3d) and click **Sign in** at the top right. (The referral code is `jmp4ee3d`.)
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All of these are free, and signing in with a wallet sends no transaction.
3. Open your profile — the avatar at the top right — and fill it in: a username, a picture, and a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet from your profile as well. Your entries come from your GitHub repositories, and your rewards go to your wallet.

## Step 2 — Connect your coding agent to your account

Your agent needs to act under your account, rather than making an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, check the code matches, and approve it. If the command stops waiting before you approve, just run it again.

The first time you do this, it also creates a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` and attaches its wallet to your account. From then on, entries sent from the kit go in under your username, and your entry and claim signatures use that wallet. You can decide what else the connection is allowed to do (commenting, betting, editing your profile) under **Profile → API keys → Paired agents**.

## Step 3 — Choose a bounty

The front page lists every bounty, grouped into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Each card shows the reward; each bounty page shows:

- **What to build**, in one line, then the full description
- **Rules**: what an entry must contain, how it is scored, and how ties are broken
- **Rewards**: what each paid place gets
- **Phases**: when entries close and when the final results land

Read the rules before you build. Some bounties need extra software or an account on another service, and their page says so up front.

## Step 4 — Download the bounty's kit

Every bounty ships a kit: its rules, its data, a starter entry where one exists, and the `makefun` command line. Get it from the entry form on the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the bounty's rules word for word. It also says whether the bounty can be graded on your own machine. Where it can, its **Grade locally** section gives the exact command, which usually looks like this, run from the kit with your entry's folder (step 5) next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry against the kit's practice data the same way the server does, in the same Docker sandbox, so you can see where you stand before you submit.

## Step 5 — Build your entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder (the commands here call it `my-entry`), and open a fresh agent session inside it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner.
4. **Build inside that session.** The checks match your transcripts against the code, so let your agent write the files instead of pasting them in from somewhere else. Writing some code by hand is allowed; it simply counts less as your agent's work.
5. **Add the README the bounty asks for.** The bounty's requirements give a README template with make.fun's badges for your repository — fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, with every command and check included.

## Step 6 — Bundle, check and submit

Push your work, note the commit you want to enter, then bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` gathers every session that worked on the repository, strips out credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and tells you which flag to add. A Claude Code log, for example, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`. (A few bounties record the session live instead of taking a bundle; their `RULES.txt` says how.)

Before you enter, run the site's own checks on your own machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 2, which every bounty with an escrowed reward asks for. That wallet is also where the reward will be paid.

## Step 7 — Follow your entry and fix rejections

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts, unless you pick an earlier one.

## Step 8 — Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Claim within 7 days of the results being posted: a prize not claimed inside that window passes to the next entry in the standings.

## Referrals: how signups are counted

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, plus a share of what they win for a while after they sign up — make.fun pays that share on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

For this contest, the same checks that pay make.fun's referral rewards decide which signups count. The window runs from the competition's opening (18 November 2026, 10:30 UTC) to its deadline (21 November 2026, 10:30 UTC):

- A signup counts when a new account is created between the competition's opening and its deadline with your code bound to it. A signup bound after the deadline does not count; one whose first touch was before the opening counts if the account is created inside the window.
- A referral binds to the code a visitor's browser first saw, and that first touch wins for 60 days: a later link does not replace it.
- It counts only when the house's referral check verifies it. A signup that is the referrer's own account, or that shares its person or its network, does not count. Neither does one from an IP cluster of signups from the same address, an idle account, a lurker that never took part, or a bot. A signup whose referral reward was rejected never counts.
- The board shows each entry's verified signups as the check verifies them; a dev count is provisional.
- The final check starts at the deadline. Each signup is decided once its own 24-hour review hold from binding has closed, and the signups verified by the end of the final check — 30 hours after the deadline — are the ones that count. A signup still undecided then does not count.
- The referral reward's cap and budget do not limit the contest score: a verified signup counts even when its referrer has already taken as many signup rewards as the program pays, or the reward budget is spent.

If this guide helped, signing up through [my link](https://make.fun/r/jmp4ee3d) (code `jmp4ee3d`) is a nice way to say thanks.

## Prizes for this contest

This contest shares **$1,000** across the 50 highest-ranked entries, paid in USDC on Solana:

| Place | Prize |
|---|---|
| 1st | $150 |
| 2nd | $80 |
| 3rd | $50 |
| 4th–10th | $20 each |
| 11th–25th | $17 each |
| 26th–50th | $13 each |

Entries rank by verified signups, highest first. An exact tie goes to the earlier receipt: the entry whose final submission was received first places first. There is one place per entrant — an entrant with two entries in the top 50 takes only the higher place.

## Frequently asked questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I let my agent do the whole thing?</strong></summary>

Yes. Open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/jmp4ee3d · code `jmp4ee3d`</sub>
