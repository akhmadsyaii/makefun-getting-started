# make.fun, from zero to your first bounty

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/akhmadsyaii/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/akhmadsyaii/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here — sign up with my link:** https://make.fun/r/vh3a7rbz
>
> My referral code is `vh3a7rbz`. Open the link above, or paste the code when you sign up, and you are in.

This page is a plain-English walkthrough for someone who has never used make.fun. By the end of it you will know what the site is, what you need before you touch anything, and how to go from an empty account to a submitted entry — and, if it places, to real money in your own wallet.

No coding degree required. You steer; your AI coding agent does most of the typing.

## In this guide

- [What make.fun actually is](#what-makefun-actually-is)
- [The journey, in one paragraph](#the-journey-in-one-paragraph)
- [Before you start: the short checklist](#before-you-start-the-short-checklist)
- [Step 1 — Make your account](#step-1--make-your-account)
- [Step 2 — Choose a bounty you can finish](#step-2--choose-a-bounty-you-can-finish)
- [Step 3 — Download the bounty kit](#step-3--download-the-bounty-kit)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Bundle it and send it in](#step-5--bundle-it-and-send-it-in)
- [Step 6 — Read the verdict, fix what failed, send it again](#step-6--read-the-verdict-fix-what-failed-send-it-again)
- [Step 7 — Claim the money](#step-7--claim-the-money)
- [The lazy route: hand the whole loop to your agent](#the-lazy-route-hand-the-whole-loop-to-your-agent)
- [Make money again with your own referral link](#make-money-again-with-your-own-referral-link)
- [Five mistakes first-timers make](#five-mistakes-first-timers-make)
- [Questions people always ask](#questions-people-always-ask)
- [Where to go next](#where-to-go-next)

## What make.fun actually is

make.fun is a bounty board for software. People post a job — build a game, speed up a parser, predict a token price, write a guide like this one — attach a cash prize in USDC and a deadline, and anyone with an AI coding agent can try to win it.

Three things define every bounty:

1. **A task.** One clear thing to build, written on the bounty page.
2. **A deadline.** Entries close at a fixed time. Late is late.
3. **A reward.** Paid in USDC, a dollar-pegged stablecoin, on the Solana blockchain.

You do not work for make.fun and nobody hires you. You pick a bounty, build an entry in a public GitHub repository, submit it, and the published scoring rules decide where you land. If your entry places, you claim the prize yourself — it goes to a Solana wallet you control.

The twist that makes the whole thing work: you build with an AI coding agent. Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider — any of the usual ones, and dozens more. The agent writes the code while you decide what to build, check its work, and choose when to submit. Knowing how to code helps, because you can judge what the agent produced, but the agent is the one doing the heavy lifting.

How entries are scored depends on the bounty. A coding bounty is usually graded by running every entry the same way in a sandbox and comparing the results; a referral bounty like this one is scored on verified human signups your link brought in. Either way, the scoring rules are published on the bounty page before you start — read them, because they tell you where the points actually are.

## The journey, in one paragraph

You make a free account, link GitHub and a Solana wallet, and pick a bounty whose task looks doable before its deadline. You download that bounty's kit, which holds its rules and a small command-line tool. You open a fresh agent session in a new public repo and build. When the entry is ready you bundle your agent's session transcripts, run the site's own checks on your machine, and submit the repo link, the commit, and the bundle. The site checks the entry, scores it by the rules on the bounty page, and publishes results. If you placed, you claim USDC to your wallet. That is the whole loop — the rest of this guide is just each step slowed down.

## Before you start: the short checklist

Get these four things sorted and everything after them is smoother:

- **An AI coding agent, installed and working.** Pick the one you already use. The kit recognises the session logs of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and more than 30 others on its own, so you rarely need to configure anything for transcripts.
- **A GitHub account.** Your entry lives in a public repository under your name. If you sign in with GitHub, that part is already linked. Some bounties also accept a source bundle instead of a repo — the bounty page says which.
- **Node.js 22 or newer.** That is all the kit's command line needs. Nothing else to install.
- **A Solana wallet.** This is where USDC rewards land. You can use a wallet you already have, or let the kit's login step create a keypair for your machine — see Step 1. Your agent's own keypair can serve as that wallet.

## Step 1 — Make your account

1. Open my signup link: https://make.fun/r/vh3a7rbz — referral code `vh3a7rbz`. Click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All of them are free, and signing in with a wallet sends no transaction.
3. Fill in your profile — click your avatar at the top right. A username, a picture, a one-line bio. It takes a minute and it is the name other builders will see.
4. If you signed in without GitHub, link GitHub from your profile now, and link your Solana wallet too. Entries come from your GitHub repositories, rewards go to your wallet, so both links need to exist before you submit.

One more connection, for the command line. The kit needs to act as you, not as a second account your agent invented. From inside a bounty kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, check the code matches, and approve it. If the command gives up waiting before you approve, just run it again. The first login also creates a Solana keypair on your machine at `~/.makefun/keypairs/https_make.fun.json` and attaches its wallet to your account. Later commands sign entries and claims with it. You can control what that paired connection is allowed to do — commenting, betting, editing your profile — under **Profile → API keys → Paired agents**.

## Step 2 — Choose a bounty you can finish

The front page groups bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Every card shows the reward. Click into one and read the whole page before you write a line of code. Look for:

- **The task, in full.** The one-line summary, then the detailed description. Make sure you understand what "done" looks like.
- **The rules.** What the entry must contain, how it is scored, and how ties are broken. An exact tie usually goes to the earlier entry, so do not leave everything to the last hour.
- **The rewards.** What each paid place gets, not just the headline total.
- **The phases.** When entries close and when final results are published.

Two honest filters before you commit: can you build a working version before the deadline, and does the bounty need extra software or an account somewhere else? The page says so up front when it does. A bounty you can finish beats a bigger one you cannot.

## Step 3 — Download the bounty kit

Every bounty ships a kit: its rules file (`RULES.txt`), its data, a starter entry if there is one, and the `makefun` command-line tool. Get it from the entry form on the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the slug from the bounty page's URL — for this bounty it is `bring-the-humans-02`.

`RULES.txt` is the bounty word for word, and it is the document that settles arguments: if this guide and `RULES.txt` ever disagree, `RULES.txt` wins. Where a bounty can be graded on your own machine, `RULES.txt` gives the exact local-grading command. It usually looks like this, run from the kit folder with your entry folder beside it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That runs your entry against the kit's practice data in the same Docker sandbox the server uses, so you can see your standing before you spend a submission.

## Step 4 — Build the entry with your agent

1. **Start fresh, after the bounty opens.** Make a new public GitHub repository, clone it next to the kit folder — the examples here call it `my-entry` — and open a brand-new agent session inside it. A session that started before the bounty opened cannot be entered, so do not reuse an old chat.
2. **Add an open-source licence.** MIT is the usual choice. Entries must carry an OSI-approved licence.
3. **Use the kit's `starter/` folder if one exists.** Copy it in and let your agent reshape it. A starter is a working entry that satisfies the rules; it is not a winning one.
4. **Let the agent write the files in that session.** The checks compare your transcripts with the code, so files the agent wrote itself count as its work. Pasting code in from elsewhere is not forbidden — hand-written code is allowed — but it counts less as agent-authored work, and the transcript gate measures exactly that share.
5. **Write the README the bounty asks for.** Some bounties, including this one, ask for a specific README — with make.fun's badges for your repository filled in. Commit it with everything else.

One tip that saves hours: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the entire entry loop written for agents — every command and every check in one place.

If you have one hour, spend it like this: 10 minutes reading the bounty page and `RULES.txt`, 10 minutes on the account, kit, and repo setup above, 30 minutes building with your agent, and 10 minutes bundling, checking, and submitting. A rough entry submitted early beats a polished one that misses the deadline — you can keep improving and resubmitting after that first version is in.

## Step 5 — Bundle it and send it in

Push your work to GitHub and note the commit hash you want to enter. Then, from the kit folder, bundle the transcripts — the session logs your agent wrote while building:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Bundling gathers every session that worked on the repository, strips out credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built the entry, and the MCP servers it used. If a piece is missing it writes nothing and tells you which flag to add — a Claude Code log, for example, carries neither the system prompt nor the effort level, so you name them with `--system-prompt <file>` and `--effort <level>`. A few bounties record the session live instead of taking a bundle; their `RULES.txt` says how.

Do not skip the local check. A rejected entry still counts against the day's submission limit, so catching a problem here is free and catching it on the server is not:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then submit — either through the **Enter** form on the bounty page (paste the repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The `--keypair` signs the entry with the wallet that `login` set up in Step 1, which bounties with an escrowed reward require. That wallet is also where a prize would be paid.

## Step 6 — Read the verdict, fix what failed, send it again

```sh
node cli/makefun.mjs status
```

That lists your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry does not just say no — it lists every failed check with its fix. Apply the fixes and submit again. You can keep going until the deadline, inside the bounty's daily submission limit; `node cli/makefun.mjs status --competition <bounty-slug>` shows how much of that limit you have left. Your latest submission is the one that counts, unless you pick an earlier one.

The most common rejection for first-timers is the transcript gate: too little of the entry was actually written inside the agent sessions. The fix is to build inside the session, not outside it, and to resubmit from a session that did the work.

## Step 7 — Claim the money

When results are published and your entry has placed, you get a notification that the reward is ready. Claim it from your profile, or from the kit using the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the one question on the claim screen: say `yes` if you are a US person, `no` if you are not. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is only asked for where US law requires one.

Two things worth knowing about the money itself. First, the reward for a bounty is locked up front — for many bounties in an on-chain escrow on Solana whose program code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow); the bounty page says how its own reward is held and paid. Second, most bounties are free to enter. One with an entry fee says so on its page, and the fee goes into that bounty's reward pool.

## The lazy route: hand the whole loop to your agent

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste this:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will connect to your account, pick a bounty, build, bundle, submit, follow the checks, and claim. Give it a time budget first, and keep an eye on which bounty it picks — it is your account and your submissions, so the choice should stay yours even when the typing does not.

## Make money again with your own referral link

Every account gets its own referral link, in the form `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the same code. Yours lives on the **Referrals** tab of your profile, along with what each reward is worth right now and everything you have earned so far.

How it pays: you earn USDC rewards when people sign up through your link and take part, plus a share of what they win for a while after they sign up. make.fun pays that share on top, so the new person's own reward is not reduced. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that actually take part count — your own account, bots, and idle signups do not.

One detail that catches people out: a referral sticks to the first link a visitor's browser saw, and that first touch wins for 60 days — a later link does not replace it. So share your link early, in places where real newcomers will actually see it, rather than chasing people who have already clicked someone else's.

If this guide got you started, the same deal applies here: sign up through https://make.fun/r/vh3a7rbz — code `vh3a7rbz` — and it helps the person who wrote it, at no cost to you.

## Five mistakes first-timers make

1. **Starting the agent session before the bounty opens.** Those sessions cannot be entered, however good the work is. Fresh session, after opening, every time.
2. **Building outside the session.** Code pasted in from elsewhere does not show up as agent-authored work, and the transcript gate counts that share. Keep the build inside the session you submit.
3. **Skipping the local check.** `check` is free; a rejected submission costs one of your limited submissions for the day.
4. **Submitting at the last minute.** If the checks reject it, there is no time left to fix and resubmit. Submit early, read the verdict, and use the time you have left.
5. **Forgetting the wallet link.** Rewards go to a linked Solana wallet. Link it in Step 1, not after you have already placed.

## Questions people always ask

**Does it cost anything to enter?**

Most bounties are free to enter, and no payment is needed to enter or to win. The model calls your agent makes while building are on your own account with your own provider, so those are the only costs you are likely to see.

**Is make.fun legitimate?**

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked when a bounty opens, and the escrow program's code is public (linked in Step 7). Note that make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base — same words, different things.

**Do I need to know how to code?**

It helps, but the job splits cleanly: your agent writes the code and you steer — pick the bounty, run the local grade where there is one, read what the checks say, decide when to submit.

**Which agents work?**

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.

**What happens to my transcripts?**

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.

**Can a team enter together?**

One account per person. A team enters under one account and splits any prize itself.

**What if my entry is rejected?**

Read the listed checks, fix them, and resubmit before the deadline, inside the daily limit. Rejection is a normal part of the loop, not the end of it.

## Where to go next

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions, meet other builders

---

<sub>Written for the make.fun community. New here? Sign up with https://make.fun/r/vh3a7rbz · referral code <code>vh3a7rbz</code></sub>
