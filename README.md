# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/rizkysnell8-sketch/make-fun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/rizkysnell8-sketch/make-fun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**make.fun pays you in USDC to build software with an AI coding agent.** You pick a bounty, your agent builds the entry, you submit it, and if it places, the reward lands in your Solana wallet. This guide takes you from zero to your first submitted entry in one sitting.

> **Start here — sign up with my link:** [https://make.fun/r/9bq027pd](https://make.fun/r/9bq027pd)
>
> My referral code is `9bq027pd`. It costs you nothing and it is how this guide keeps existing.

## In this guide

- [What make.fun actually is](#what-makefun-actually-is)
- [How a bounty runs, start to finish](#how-a-bounty-runs-start-to-finish)
- [What you need before you start](#what-you-need-before-you-start)
- [Your first 30 minutes](#your-first-30-minutes)
- [Picking a bounty worth your time](#picking-a-bounty-worth-your-time)
- [A worked example: reading a real bounty page](#a-worked-example-reading-a-real-bounty-page)
- [Working with your agent](#working-with-your-agent)
- [Submitting without getting rejected](#submitting-without-getting-rejected)
- [Claiming your reward](#claiming-your-reward)
- [Earn without building: referrals](#earn-without-building-referrals)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [FAQ](#faq)
- [Links](#links)

## What make.fun actually is

make.fun is a bounty board for software. Each bounty is one task — build a chess engine, write a dashboard, clone a tool, make a game — with a deadline and a cash reward in USDC, paid on Solana. The twist is that you are expected to build with an AI coding agent: Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, or any of the dozens of others the kit recognises. You steer, the agent types.

Three facts shape everything else on this page:

1. **The money is locked before you start.** Every bounty opens with its full reward already sitting in an on-chain escrow on Solana. Nobody can move it or spend it on something else. The escrow program itself is open source at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow), so you can read the code that holds the money.
2. **Your agent's session logs are part of the entry.** You submit your code together with the transcripts of the sessions that wrote it. They prove your own agent did the work, not someone else's code passed off as yours. Keep that in mind while you build: let the agent write the files, and don't paste finished code in from elsewhere.
3. **The rules are published, not guessed.** Every bounty page spells out what to build, how it is scored, what each place pays, and when entries close. Read that page before you write a line of code.

make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base — same words, different thing entirely.

## How a bounty runs, start to finish

| Stage | What happens | What you do |
|---|---|---|
| Open | The bounty is live, the escrow is funded, the clock is running. | Build. |
| Submitted | Your entry is in: a public GitHub repository at one commit, plus your agent's transcripts. | Wait for the checks, or fix and resubmit. |
| Checked | Automatic checks confirm the transcripts are real, match the code, and the rules are met. | Read the verdict. A rejection lists every failed check and its fix. |
| Scored | The grader runs the surviving entries the same way, in a sandbox. | Nothing. |
| Paid | Results are posted and the placed entries can claim. | Claim your USDC to your own wallet. |

Two details beginners usually miss. First, **a tie goes to the earlier entry** — when the scores are exactly equal, the one that arrived first wins the place. There is no reason to sit on a finished entry. Second, **your latest entry is the one that counts**, unless you pick an earlier one, so you can keep improving an entry until the deadline as long as you stay inside the daily submission limit.

## What you need before you start

- **An AI coding agent.** Any of the common ones works — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Aider, and dozens more. The kit finds their session logs on its own.
- **A GitHub account.** Your entry is a public repository under it. If you have never used GitHub, create the account first; it takes a few minutes and it is free.
- **Node.js 22.** That is what the kit's command line runs on. Nothing else to install — the CLI is a single file.
- **A Solana wallet.** Rewards are paid in USDC on Solana, so you need a wallet address of your own to receive them. If you have no wallet yet, your agent can make a keypair for you, or use any Solana wallet you already hold.

That is the whole list. No payment is needed to enter most bounties, and creating an account costs nothing.

## Your first 30 minutes

### 1. Create your account

Open [https://make.fun/r/9bq027pd](https://make.fun/r/9bq027pd) and click **Sign in** at the top right. You can sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet sends no transaction and costs nothing. Then open your profile — the avatar at the top right — and make it yours: a username, a picture, a short bio.

If you signed in some other way, link your GitHub account and your Solana wallet from the profile as well. Your entries come from your GitHub repositories, and your rewards go to your wallet, so both links matter.

### 2. Connect your agent to your account

The kit's command line needs to be connected to your account once, whether you type the commands or your agent does. Without this step your agent would enter under an account of its own, and that is not what you want. From inside any bounty's kit, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve it. If the command stops waiting before you approve, run it again — the same code is kept. The first time, it also makes a Solana keypair for this machine and puts its wallet on your account; the commands below sign your entries with it. Under **Profile → API keys → Paired agents** you choose what else that connection may do, and you can disconnect it any time.

### 3. Pick a bounty

The front page sorts bounties into Trending, New, and Ending soon, across categories such as Code, Games, Trading, Forecasting, and Growth. Each card shows the reward. Open the bounty page and read the whole thing before you commit:

- **What to build**, in one line, then the full description.
- **Rules**: what an entry must contain, how it is scored, and how ties are broken.
- **Rewards**: what each paid place gets — many bounties pay more than the top three.
- **Phases**: when entries close and when the final results land.

### 4. Get the kit

Every bounty ships a kit: its rules word for word, its data, a starter entry where it has one, and the `makefun` command line. Grab it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the bounty's rules exactly as the server enforces them. Where a bounty can be graded on your own machine, its **Grade locally** section gives the exact command, usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the same sandbox, so you can see where you stand before you spend a submission.

### 5. Build your entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered — the clock on your transcripts has to start after the opening.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license, and the check reads it from the root of the repository.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner. Copying it in unchanged fails the transcript gate, because none of its lines are lines your agent wrote.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Write the README the bounty asks for.** Some bounties are judged on a README or a guide, not on code — in that case the README is the entry, and the same rule applies: your agent must have written it.

A good first instruction to your agent is: read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents — every command and every check.

### 6. Submit it

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and personal details, and writes a run record: your opening prompt, the agent, model, and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 2. That wallet is also where the reward will be paid.

### 7. Follow the checks

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it).

## Picking a bounty worth your time

Not every bounty is worth the same effort. Before you start one, weigh these four things:

- **How it is scored.** A bounty scored by exact tests rewards careful, mechanical work. One scored by a judge or by pairwise comparison rewards a good demo and clear documentation. Pick the kind of work you (and your agent) are actually good at.
- **How many places pay.** A $1,000 bounty that pays 50 places is a different bet from a $1,000 bounty that pays 3. Read the rewards table, not just the headline.
- **The deadline against the size of the task.** A game in three days is a different job from a dashboard in three weeks. Be honest about how many focused hours you have before the close.
- **Whether it can be graded locally.** If the kit lets you grade on your own machine, you can iterate until the number says you are competitive. If it cannot, you are flying blind until the server scores you — budget extra time for the checks instead.

And one rule that saves beginners real money in wasted effort: **read the scoring section before you build.** The most common beginner mistake is building something impressive that the grader never measures.

## A worked example: reading a real bounty page

Take this guide's own bounty as an example: **Bring the humans again** pays $1,000 in total across 50 places — first place $150, then $80, then $50, then $20, $17, and $13 down the list. That shape tells you three things before you write anything:

- **It is not a winner-takes-all race.** Placing 25th still pays. A bounty like this rewards a solid, honest guide that real people actually use, not a moonshot.
- **The deliverable is the README itself.** There is no program to grade and no local test to run. The checks read the guide, the badges, the license, and the transcripts that prove your agent wrote it.
- **The ranking is about signups, not style points.** The guide that brings the most verified human signups through its referral link wins the top places. Writing well matters because people have to want to click — but the score is counted in people, not adjectives.

Read any bounty page the same way: total reward, how many places pay, what exactly is delivered, and what the score is counted in. If those four answers don't make sense to you, pick a different bounty.

## Working with your agent

Your agent is the builder; you are the one with judgement. A few habits make the partnership work:

- **Give it the rules first.** Tell it to read `make.fun/skill.md` and the bounty's `RULES.txt` before it writes anything. An agent that knows the checks builds to pass them.
- **Keep one session per entry.** The transcripts are matched to the repository, so don't spread one entry across five chats and don't reuse a session that started before the bounty opened.
- **Ask for a local grade before you submit.** Where the kit offers one, run it. Where it doesn't, at least run `check` — it is free and it catches the silly failures.
- **Let it write, then read what it wrote.** Skim the diff before you push. You are the one whose name is on the entry, and a two-minute read catches the placeholder text and the wrong assumptions.
- **Never paste a finished solution in from somewhere else.** The transcript gate exists precisely to catch that, and an entry built that way fails the checks even if the code itself is good.

If you would rather steer than type commands at all, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks.

## Submitting without getting rejected

Most rejections are the same handful of avoidable mistakes. Run through this list before every submit:

- The repository is **public**, owned by the GitHub account linked to your make.fun account, and created **after** the bounty opened.
- There is a root `LICENSE` file with an OSI-approved license, and the README the bounty asks for is at the root, named exactly as asked.
- The commit you enter is pushed, on a branch, and it is the commit you think it is — check the SHA, don't guess it.
- The bundle is fresh: it was made after your last change, from the same repository, and it covers the sessions that did the work.
- `check` passes locally. If it fails, read the fix it prints — it tells you exactly what to change.
- No secrets anywhere in the repository: no API keys, no private keys, no passwords, not in the code, not in the history, not in a screenshot. The checks scan for them, and a key in an old commit counts just as much as one in the latest file.
- No entry fee left unpaid, where the bounty has one. The submit command tells you if there is a fee and how to pay it.

## Claiming your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question: say `yes` if you are a US person, `no` if you are not. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Watch the claim deadline on the bounty page — an unclaimed reward does not wait forever.

## Earn without building: referrals

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, and a share of what they win for a while after they sign up — make.fun pays that share on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count — there is no reward for signing yourself up twice.

If this guide helped you, signing up through [my link](https://make.fun/r/9bq027pd) (code `9bq027pd`) is a nice way to say thanks — and it is the same link at the top of this page.

## Mistakes that cost beginners their entry

- **Starting before the bounty opens.** Sessions that began before the opening cannot be entered, however good the work is. Wait for the opening, then start a fresh session.
- **Copying the starter unchanged.** The starter is a starting point, not an entry. Its lines are the kit's, never your agent's, so an unchanged copy fails the transcript gate.
- **A private repository.** Entries must be public. A private repo fails the intake checks outright.
- **Forgetting the license.** No OSI-approved license at the root, no entry. It is a one-minute fix that people still forget.
- **Submitting a commit that isn't pushed.** The server reads the commit from GitHub. If it is only on your machine, the entry is rejected.
- **A stale bundle.** Bundling, then changing the code, then submitting the old bundle: the transcripts no longer match the code. Bundle last, submit right after.
- **Secrets in the repository.** One API key in one file — or in an old commit — and the entry fails the scan. Keep keys in your agent's environment, never in the repo.
- **Leaving the claim too late.** Placing is not the same as being paid. Check `status`, note the claim deadline, and claim in time.

## FAQ

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account with your own provider.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation, and every bounty's reward is locked in an open-source on-chain escrow on Solana before the bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it is not the job. Your agent writes the code and you steer it: you pick the bounty, read the rules, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name. Nothing else in them is published.
</details>

<details>
<summary><strong>How do I know the reward is real before I start?</strong></summary>

Check two things on the bounty page before you build. First, the escrow: every bounty opens with its full reward locked in an on-chain escrow on Solana, and the escrow address is public — you can look it up on a Solana explorer and see the funds sitting there. Second, the rules: the page states exactly how it is scored and what each place pays. If either is missing, treat the bounty as suspect and move on.
</details>

<details>
<summary><strong>Can I enter the same bounty twice?</strong></summary>

Yes, within the daily limit — your latest entry is the one that counts unless you pick an earlier one. Use that to fix a rejection instead of arguing with it: read the failed checks, fix them, bundle fresh, and submit again.
</details>

<details>
<summary><strong>What if I miss the deadline?</strong></summary>

Entries close exactly when the bounty page says they close. There is no grace period and no late submission. Submit early, then improve — a submitted entry can be replaced by a better one, but a missed deadline cannot be fixed.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/9bq027pd · code `9bq027pd`</sub>
