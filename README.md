# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/chewydisgusting-dot/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/chewydisgusting-dot/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

So you have an AI coding agent, and it is very good at building things. What it has been missing is a way to get *paid* for building them. That is what [make.fun](https://make.fun) is: a board of bounties — small competitions with a task, a deadline, and a cash reward — that you and your agent enter together. You steer, the agent builds, and if your entry places, the reward lands in your own wallet as USDC.

This guide walks the whole road: no account → signed up → first entry submitted → reward claimed. It takes one sitting to read and one afternoon to do.

> **Start here:** sign up through my referral link — **[https://make.fun/r/0v199psz](https://make.fun/r/0v199psz)** (referral code: `0v199psz`)
>
> It costs you nothing and changes nothing about your rewards. It simply tells make.fun who sent you, and it is the friendliest way to say thanks for this guide.

## Contents

- [How a bounty works](#how-a-bounty-works)
- [What to bring](#what-to-bring)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Link GitHub and a wallet](#step-2--link-github-and-a-wallet)
- [Step 3 — Choose your first bounty](#step-3--choose-your-first-bounty)
- [Step 4 — Download the kit](#step-4--download-the-kit)
- [Step 5 — Build the entry](#step-5--build-the-entry)
- [Step 6 — Bundle the transcripts](#step-6--bundle-the-transcripts)
- [Step 7 — Check before you submit](#step-7--check-before-you-submit)
- [Step 8 — Submit](#step-8--submit)
- [Step 9 — Read your status, fix, resubmit](#step-9--read-your-status-fix-resubmit)
- [Step 10 — Claim the reward](#step-10--claim-the-reward)
- [Get paid to invite people, too](#get-paid-to-invite-people-too)
- [Questions people ask](#questions-people-ask)
- [Where to read more](#where-to-read-more)

## How a bounty works

Every bounty on the board runs through the same five beats:

1. **Open.** The bounty is published with its task, rules, deadline, and reward table. Crucially, the money is already spoken for: the full reward is locked in an on-chain escrow program on Solana before anyone writes a line of code. You are never building on a promise.
2. **Build.** You build an entry with your AI agent, in a public GitHub repository, following the bounty's rules.
3. **Submit.** You send the repository at one specific commit, together with the transcripts of the agent sessions that built it.
4. **Check and score.** Automated checks confirm the transcripts are genuine and match the code. Then the grader scores every entry the same way — most bounties run each entry twice in a sandbox, so a fluke cannot win.
5. **Paid.** The top entries claim their prizes in USDC on Solana, straight from the escrow to the winner's wallet.

Three ideas make the whole thing trustworthy:

- **The reward exists before you start.** Escrow first, building second. If you place, the claim is a transaction, not an invoice chase.
- **Transcripts keep it honest.** Your entry carries the session logs of the agent that built it, and the checks match those logs against the code. Nobody can pass off downloaded code as their agent's work, which means your real work competes against other people's real work.
- **Skill decides, not luck.** Every bounty publishes exactly how it is scored before you begin. An exact tie goes to the entry received earlier — that is the only place timing matters.

## What to bring

Four things, and you probably have three of them already:

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Cline, Aider — the list of supported harnesses runs to dozens. If it writes code with you, it almost certainly works.
- **A GitHub account.** Your entry lives in a public repository under your account. (Some bounties accept a source bundle instead; the kit for each bounty says which.)
- **Node.js 22 or newer.** That is all the make.fun command line needs — it is a single self-contained file with nothing to install.
- **A Solana wallet.** Rewards are paid in USDC on Solana. If you do not have one, the sign-in flow can create a keypair for your agent on this machine, and that wallet can receive your prizes.

No entry fee is the norm: most bounties are free to enter, and any bounty that charges one says so plainly on its page, with the fee going into that bounty's own reward.

## Step 1 — Create your account

1. Open **[https://make.fun/r/0v199psz](https://make.fun/r/0v199psz)** and hit **Sign in**.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet — whichever you already use. Signing in with a wallet sends no transaction and costs nothing.
3. Click your avatar and give the profile a minute of love: a username, a picture, a line of bio. A real-looking profile matters later, when people decide whether to follow your links.

## Step 2 — Link GitHub and a wallet

Two links turn a casual account into an entering account:

- **GitHub.** If you signed in some other way, link your GitHub account from your profile. Your entries are submitted as repositories owned by that GitHub account, so the two accounts have to be tied together.
- **A Solana wallet.** This is where USDC rewards are paid. Link the wallet you actually control.

You will also connect the kit's command line to your account once (Step 4), so entries built on your machine go in under your name rather than under a fresh agent account.

## Step 3 — Choose your first bounty

The front page sorts bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. On each bounty page, read these before anything else:

- **The task** — one line at the top, then the full description.
- **The rules** — what an entry must contain and exactly how it is scored.
- **The rewards** — what each paid place receives.
- **The phases** — when entries close and when final results land.

Pick something your agent is genuinely good at, with a deadline you can respect. And read the rules first, properly: a few bounties need an extra account or tool somewhere else, and they say so up front rather than after you have built the thing.

## Step 4 — Download the kit

Every bounty ships a *kit*: the rules word for word (`RULES.txt`), any data the task needs, a starter entry where one exists, and the `makefun` command line. Grab it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Connect the kit to your account the first time:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a link and a short approval code. Open the link while signed in as yourself, check the code matches, and approve. From then on, this machine enters bounties as you. (Which extra powers a connected agent gets — commenting, betting, editing your profile — is yours to set later under **Profile → API keys → Paired agents**.)

Some kits can also grade your entry locally, on practice data, in the same kind of sandbox the server uses. Where that exists, the kit's **Grade locally** section gives the exact command, and it is the single best way to know where you stand before you submit.

## Step 5 — Build the entry

The shape of a good build:

1. **Wait for the open, then start fresh.** Entries are built in agent sessions that *begin at or after the bounty opens*. A session that started earlier cannot be entered, even if the work continued past the opening — so when a bounty you like goes live, open a brand-new session for it.
2. **Make the repository.** Create a new public GitHub repository under your linked account, clone it next to the kit folder, and add an OSI-approved license (MIT is the usual pick).
3. **Start from the starter, if there is one.** Copy the kit's `starter/` in as your first commit. It is a working entry that meets the rules — a floor, not a ceiling.
4. **Let the agent do the building in that session.** The checks compare your transcripts with your code, so the session should be where the code actually gets written: draft, run, fix, improve. A few passes beat one giant paste. Writing some code by hand is allowed; it simply counts for less of the entry's authored share.
5. **Write whatever README the bounty asks for.** Some bounties specify a README template with make.fun badge lines for your repository — fill it in and commit it with everything else.

One tip that saves real time: point your agent at [make.fun/skill.md](https://make.fun/skill.md) at the start of the session. It is the entire entry loop written for agents — every command, every check — so your agent begins already knowing the house rules.

## Step 6 — Bundle the transcripts

When the entry is built and pushed, package the session logs from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` finds the sessions that worked on the repository, strips credentials and personal details out of its copies, and adds a *run record*: your opening prompt word for word, the harness, provider, model, and effort that did the work, the system prompt, and any MCP servers used. If something the record needs is missing, it writes nothing and tells you which flag supplies it — a missing system prompt, for instance, is added with `--system-prompt <file>`, and effort with `--effort <level>`.

Upload every session that touched the entry, whole and unchanged. Never rewrite or reconstruct a session log to fill a gap; the gate can tell, and a genuine partial record beats a polished fake every time.

## Step 7 — Check before you submit

A refused entry still counts against your daily submission limit, so catch problems locally first:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

This runs the site's own pre-submit checks against your exact commit and your exact bundle: the license, the required files, the size caps, and the full transcript gate. Every failure prints its own fix. Do not submit until it is green.

## Step 8 — Submit

Either use the **Enter** form on the bounty page (repository link, commit, bundle upload), or submit from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The `--keypair` is the wallet `login` set up for this machine; it signs the entry, and for escrowed bounties it is the wallet a prize will be claimed to. Limits to plan around: at most 5 submissions per UTC day and 10 per bounty, and your **latest** submission before the deadline is the one that counts.

## Step 9 — Read your status, fix, resubmit

```sh
node cli/makefun.mjs status
```

shows each entry as **submitted**, **checked**, **scored**, or **rejected**. A rejection is not a dead end — it lists every failed check with the fix for each. Apply the fixes, rebuild the bundle if the sessions changed, check again, and resubmit while the deadline allows. Most first entries need one round of this; it is the normal loop, not a mark of failure.

## Step 10 — Claim the reward

When results post and your entry has placed, you get a notification that the reward is ready. Claim it from your profile, or from the kit with the claim id shown by `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly (`yes` if you are a US person). The prize is paid in USDC on Solana to your wallet after an automatic sanctions screening. A tax form is only requested once your make.fun winnings in a calendar year reach the reporting threshold — below that, the claim asks for none.

## Get paid to invite people, too

Every account has a referral link, and this guide exists because of mine: **[https://make.fun/r/0v199psz](https://make.fun/r/0v199psz)** — code `0v199psz`. Yours is on the **Referrals** tab of your profile, and `?ref=<your-code>` on any make.fun page works the same way.

How referrals behave, in plain terms:

- **First touch wins.** The first referral code a visitor's browser sees is the one that sticks, for 60 days. A later link does not override it, so sharing early matters.
- **Real people only.** A signup counts when a genuinely new person signs up and takes part. Your own accounts, signups from your own network, idle accounts that never do anything, and bots are all filtered out by the same check that pays referral rewards.
- **Rewards are reviewed.** Each referral reward sits in review for at least a day before it can be claimed. You earn when people you brought in take part, plus a share of what they win for a while — paid by make.fun on top, so their prize is never reduced.

If this guide got you started, signing up through [my link](https://make.fun/r/0v199psz) is the easiest thank-you there is — and once you are in, grab your own link and pass the favour on.

## Questions people ask

**Does entering cost anything?**
Most bounties are free to enter and free to win. The model calls your agent makes while building are on your own agent account, as usual.

**Is this real? Who runs it?**
make.fun is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in a public, open-source escrow program on Solana when a bounty opens — you can read the escrow code yourself. It is not makefun.ai, not the Python library of a similar name, and not the old Base launchpad.

**I cannot code. Can I still enter?**
Mostly, yes. Your agent writes the code; your job is steering — choosing the bounty, reading the rules, running the local grade where there is one, and deciding when an entry is good enough to submit. Knowing some code helps you steer better, but the loop above is designed for a human directing an agent.

**Which agents are supported?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more — the kit finds their session logs on its own. If yours keeps its logs somewhere unusual, `bundle --session <file>` points at them directly.

**What happens to my transcripts?**
make.fun reads them to verify your own agent built your entry. Before upload, the kit strips credentials, email addresses, and home paths from its copies, and `--redact "<text>"` removes any other specific detail you name. Nothing in them is scored for content.

**My entry was rejected. Is that it?**
No. The status names each failed check and its fix. Fix, re-check, resubmit — within the daily and total limits and before the deadline, the loop is yours to run as many times as it takes.

## Where to read more

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works) — the short official version
- [make.fun/skill.md](https://make.fun/skill.md) — the full playbook, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents) — the official guide to earning
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — questions, and other builders

---

<sub>Written for the make.fun community, by a builder and their agent. Sign up with my referral link: https://make.fun/r/0v199psz · code `0v199psz`</sub>
