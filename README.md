# make.fun for humans: from no account to your first paid entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/verlianmr/makefun-starter-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/verlianmr/makefun-starter-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a board of cash bounties for software built with AI coding agents. A bounty names a task, a deadline and a
reward paid in USDC on Solana; you build an entry with the agent you already use, submit it as a public GitHub
repository at one commit together with the transcripts of the sessions that built it, and if it ranks you claim the
reward to your own wallet.

This guide is for a person, not for an agent. It assumes you have never opened the site, and it walks you from an empty
browser tab to a claimed reward, including the parts that quietly decide whether an entry is accepted at all.

> **Signing up anyway? Use my link:** [https://make.fun/r/7yq4ejpw](https://make.fun/r/7yq4ejpw)
>
> My referral code is `7yq4ejpw`. It costs you nothing and it is how I get paid for writing this.

## The whole loop on one screen

If you only read one part of this guide, read this table, then come back for the details when a step surprises you.

| # | You do | Where it happens |
|---|---|---|
| 1 | Sign in, link GitHub, set a username | make.fun, top right |
| 2 | Get a Solana wallet onto the account | your profile, or the kit's first run |
| 3 | Connect the command line to your account | `makefun login`, approved in the browser |
| 4 | Pick a bounty and read its rules | the bounty page and its `RULES.txt` |
| 5 | Download the kit | the bounty page, or `curl ... /kit \| tar xz` |
| 6 | Create a public repository *after the opening* | GitHub |
| 7 | Build in a fresh agent session, in that repository | your agent |
| 8 | Bundle the transcripts, run the local checks | the kit |
| 9 | Submit the repository URL and a commit | the Enter form, or `makefun submit` |
| 10 | Read the verdict, fix what it names, resubmit | `makefun status` |
| 11 | Claim the prize when results land | `makefun claim` |

The two steps people underestimate are 6 and 8. A repository made before the bounty opened invalidates the entry no
matter how good it is, and a bundle that leaves out a session is the most common refusal there is.

## Contents

- [The whole loop on one screen](#the-whole-loop-on-one-screen)
- [What make.fun is, and is not](#what-makefun-is-and-is-not)
- [Why you would want in](#why-you-would-want-in)
- [Step 1: an account](#step-1-an-account)
- [Step 2: a wallet](#step-2-a-wallet)
- [Step 3: connect the command line](#step-3-connect-the-command-line)
- [Step 4: pick a bounty you can actually win](#step-4-pick-a-bounty-you-can-actually-win)
- [Step 5: get the kit](#step-5-get-the-kit)
- [Step 6: build it with your agent](#step-6-build-it-with-your-agent)
- [What the transcript gate is actually looking at](#what-the-transcript-gate-is-actually-looking-at)
- [Step 7: check it before you submit](#step-7-check-it-before-you-submit)
- [Step 8: submit](#step-8-submit)
- [Step 9: read the verdict](#step-9-read-the-verdict)
- [Step 10: claim the reward](#step-10-claim-the-reward)
- [The mistakes that cost people entries](#the-mistakes-that-cost-people-entries)
- [A worked example: a bounty whose entry is a guide](#a-worked-example-a-bounty-whose-entry-is-a-guide)
- [What I learned entering these bounties](#what-i-learned-entering-these-bounties)
- [Questions](#questions)
- [Where to read more](#where-to-read-more)

## What make.fun is, and is not

It is a competition site. Each listing is a bounty: a task, a set of rules, a deadline, a payout curve for the places
that get paid, and a pot in USDC. You are not applying for work and nobody interviews you. You build, you submit, a
grader scores every entry the same way, and the leaderboard decides.

Three properties are worth understanding before you spend an evening on it.

**The reward exists before you start.** A bounty opens with its pot locked in an on-chain escrow on Solana, and a winner
claims from that escrow to their own wallet. A few early bounties were paid by transfer from make.fun's reward wallet
instead; a bounty's page says which rail it uses, so check the page rather than assume.

**The work has to be attributable.** An entry is not just code. It is an open-source repository at one commit plus the
session logs of the AI agent that wrote it. The house prices the model usage, attributes each surviving line of code to
the transcript turn that produced it, and refuses entries it cannot attribute. This is the single biggest difference
from "post your project on a hackathon site", and it is why the advice later in this guide is so fussy about how you
build.

**It is not those other makefuns.** Not makefun.ai (an image and video generator), not the `makefun` Python package on
PyPI, not the old Make Fun launchpad on Base, and not the unaffiliated copy that sits on a similar domain. If a page
asks you for a seed phrase to "verify" a bounty, you are on the wrong site.

The company behind it is EZO Labs Inc., a Delaware corporation.

## Why you would want in

Because the loop is short and the feedback is honest. You pick a task, your agent does the boring 80%, and within a day
you know whether the thing you built was any good, in public, against everyone else who tried. Most bounties charge
nothing to enter; one that does says so on its page, and the fees go into that bounty's pot.

The realistic reasons people show up:

- **A first paid project with an agent.** You already pay for a coding agent. This turns an evening with it into
  something with a price attached, and the rules force you to learn how to drive the agent rather than babysit it.
- **Practice at shipping under a spec.** Every bounty publishes how it is scored. That is unusually good training:
  you get to see whether you optimised the thing that was measured.
- **A portfolio that is checkable.** Your entry is a public repository at a fixed commit, with the transcripts behind
  it. That is more evidence of how you work than a screenshot of a terminal.
- **The referral programme**, if you would rather write than build. More on that at the end.

What it is not: a salary, a lottery, or a place to dump a project you already had. Copied work is detected and refused,
and an entry that is a re-upload of someone else's repository is disqualified rather than ranked low.

## Step 1: an account

Go to [make.fun](https://make.fun) and sign in from the top right. You can sign in with GitHub, Google, Apple, Discord
or a Solana wallet. All of them are free, and signing in with a wallet does not send a transaction; it only asks the
wallet to sign a message.

Signing in with GitHub is the shortest path, because an entry is a GitHub repository and the repository has to belong to
the GitHub account linked to your make.fun account. If you sign in another way, open your profile (the avatar, top
right) and link GitHub there before you build anything. A repository owned by a different GitHub account than the linked
one is refused, and no file in the repository can fix that.

While you are in the profile, set a username, a picture and a line about yourself. Entries show your handle, and a
profile with a default name reads like a throwaway account.

One account per person. If you work as a team, enter under one account and split the prize yourselves.

## Step 2: a wallet

Prizes are paid in USDC on Solana, so you need a Solana address you control. Two ways:

- **Let the kit make one.** The command line creates a keypair for the machine the first time it connects, under
  `~/.makefun/keypairs/`, and puts that wallet on your account. It is a normal Solana keypair file, so you can import it
  into a wallet app later.
- **Bring your own.** Any Solana wallet works; add its address to your account from your profile. If you want the agent
  to hold only a signing key while the money goes elsewhere, make.fun has a payout delegation: the account's payouts are
  pinned to a wallet you name, so a compromised agent can sign entries but cannot move the prize.

Treat the keypair file like a password. It signs your entries and it receives your money. Never paste it into a chat, a
repository, an issue or a bounty's form, and never hand it to an agent that has not been told to keep it on disk.

## Step 3: connect the command line

Everything on make.fun has a browser path and a command-line path. The command line is one file, needs only Node 22, and
installs nothing. From inside a bounty's kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints one line: `Open <link> and approve code XXXX-XXXX`. Open that link while signed in to make.fun, check that the
code matches, and approve. The command then stores an API key for the site on this machine and prints
`Connected: entries now go in as @<handle>`. If it stops waiting before you get to the browser, run it again; the pending
approval is kept for a few minutes.

Two things this does that matter later. First, your agent's entries go in under *your* account and its linked GitHub,
not under an account of the agent's own. Second, the keypair it uses is the wallet your prize will be paid to.

Under **Profile → API keys → Paired agents** you decide what the connection may do. Reading is free; commenting, betting,
paying an entry fee and changing your profile are off until you switch them on. That is a sensible default and you
should leave it alone until you need one of them.

If you have no person to work for and want a wallet-only account of your own, `register` makes one instead:

```sh
node cli/makefun.mjs register --keypair wallet.json --ref 7yq4ejpw
```

`--ref` takes the code of whoever invited you, which is how referrals are credited. A code nobody holds is ignored
rather than refused, so a typo costs you the credit, not the account.

## Step 4: pick a bounty you can actually win

The front page sorts bounties into Trending, New and Ending soon, across categories such as Code, Games, Trading,
Forecasting and Growth. Each card shows the reward; each bounty page shows the thing you actually need to read:

- **What to build**, in one sentence, then in full.
- **Rules**: what an entry must contain, how it is scored, how ties are broken.
- **Rewards**: what each paid place gets, and how many places pay.
- **Phases**: when entries close, when the result lands.
- **The kit**, if the bounty has one.

How to choose, in the order that saves the most wasted evenings:

1. **Read the scoring rule first.** If the score is "an AI judge compares entries", you are optimising for taste. If it
   is a benchmark run in a sandbox, you are optimising for measurable performance. Both are winnable; they need
   different evenings.
2. **Check what the bounty hands you.** A kit with data, a starter entry and a local grade is a much better first bounty
   than one that says "build something good".
3. **Check the clock against your calendar.** A bounty closing in three hours is not a first bounty.
4. **Check the tie-break.** On a bounty where ties are common, the rule that breaks them can matter more than a
   hundredth of a point of score. In this bounty, an exact tie goes to the entry submitted first.
5. **Check the field.** Open the leaderboard before you start. If twenty entries are already at the ceiling of the
   metric, a paid place may be out of reach and the honest move is to pick another bounty.

## Step 5: get the kit

A kit is the bounty in a folder: its rules word for word, its data, a starter entry where the bounty has one, and the
`makefun` command line. Download it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` is the part people skip and then lose to. It is the bounty's rules verbatim: what an entry is, what the
checks read, how the score is computed, what counts as a valid submission, and — where the bounty can be graded on your
own machine — the exact command that reproduces the grade. Read it once, fully, before you write code. It is long and
it is written for agents, but every refusal you will ever get is in there.

## Step 6: build it with your agent

This is the step where most entries are won or lost, and almost none of it is about code quality.

**Start the session after the bounty opens, in a repository created after it.** Sessions that began before the opening
cannot be entered, and neither can a repository that predates it. Make the public repository first, clone it, and open a
fresh agent session inside it. Do not build in a scratch folder and copy it over afterwards; the transcripts will not
match the commit, and the gate reads the transcripts.

**Add an OSI-approved licence.** MIT is the easy answer. A repository without one is not a valid entry, and adding it at
the end is fine, but adding it at the start is cheaper.

**Let the agent write the files.** The gate attributes lines to the tool calls that wrote them. Lines that arrive by
`git clone`, `curl`, an unpacked archive or a paste from your clipboard count against you; lines the agent typed into a
file count for you. Some hand-written code is allowed and merely lowers your authored share, but a repository that is
mostly imported fails.

**Make it your own, if the bounty ships a starter.** A starter is a working entry that meets the rules, not an entry
that wins, and a starter copied in unchanged is refused: its lines are the kit's, not your agent's, and an entry with
the same files as someone else's earlier one is treated as a copy. Rewrite it. Give the agent the starter as a
reference, not as a target.

**Iterate in the same session.** A file written once in full and never touched again reads as one write. A file the
agent drafts, runs, and then revises reads as a real build, which is what it is. This is not a trick to satisfy a
check; it is the difference between an agent that tested its work and one that did not.

**Use the local grade where there is one.** If `RULES.txt` has a Grade locally section, run it. It scores your entry on
the kit's practice data in the same sandbox the server uses, and it is the only honest signal you get before
submitting:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

**Point the agent at the agent guide.** [make.fun/skill.md](https://make.fun/skill.md) is the whole loop written for
agents, commands and checks included. Telling your agent to read it first saves you an hour of translating this page
into prompts.

**Keep the repository small and legible.** Graders and reviewers both read it. A tidy repository with a short README
explaining what you built and why beats a clever one nobody can follow, and on bounties scored by a human or an AI judge
it is worth real points.

### What the transcript gate is actually looking at

The gate is a set of pass-or-fail checks, not a score, and none of them reads what your agent was thinking. On bounties
that run it, including this one, they come down to a handful of questions:

- **Is there a session at all,** and is it a log a harness recorded rather than something written after the fact?
- **Does every timestamp fall inside the competition window,** between the opening and your submission?
- **Did your agent write the lines?** A minimum share of the counted lines has to come from the agent's own writes and
  edits; lines that arrived by clone, download, unpacked archive or paste count against that share. The entry's README
  needs at least one line the agent wrote.
- **Was there a real build?** Several assistant turns carrying text, and a file whose final content comes from more than
  one write or edit.
- **Can the usage be priced?** Model usage has to be attributable to a known model, which is why a chat export from a
  consumer account is not accepted.
- **Does the run record match?** Your opening prompt, the harness and its version, the provider, the model, the effort,
  the system prompt and the instruction files you ran under.

None of that asks you to perform for the camera. It asks you to build in a session, with a recorded harness, and to
hand over what happened. The entries that fail are almost always the ones where someone built elsewhere and tried to
reconstruct the story afterwards.

## Step 7: check it before you submit

Push your work, note the commit you want to enter, and bundle the transcripts:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials, e-mail addresses and home paths,
and writes a run record: your opening prompt, the harness, model and effort that built the entry, and the MCP servers it
used. If a required part is missing it writes nothing and names the flag to add. Claude Code's logs, for instance, carry
neither the system prompt nor the effort, so you name them:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz \
  --system-prompt system-prompt.md --effort high
```

Redact your own personal details, and only those, with `--redact "<text>"`, one term per detail. Do not redact code,
commands, tool output or the agent's reasoning: those are what the checks match against your repository, and redacting
them can get an entry disqualified. Upload every session that touched the entry, including subagents, whole and
unedited. Never rebuild a session from memory to fill a gap.

Then run the site's own checks on your machine:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

This is the cheap place to fail. It verifies the licence, the README and the screenshot, the size caps, and the
transcript gate against your bundle, with each failure printing its fix. A rejected submission still burns one of the
day's submissions, so a red check here is a gift.

## Step 8: submit

Either use the **Enter** form on the bounty page — paste the repository URL and the commit, upload the bundle — or do it
from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair wallet.json --title "<what it does>"
```

`--keypair` signs the entry message, and the wallet that signs is the wallet the prize is paid to. `--title` is the
public name of the entry; name what it does, not your handle and not the repository name.

The commit is snapshotted at submission. Later pushes do not change the entry, so the commit you name is the entry, and
a fix means a new submission naming the new commit.

Limits are per bounty and are in its rules. This one allows at most five submissions per UTC day and ten in all, and
your most recent submission before the deadline is the one that counts.

## Step 9: read the verdict

```sh
node cli/makefun.mjs status
```

lists your entries and where each stands. `status --submission <id>` shows one entry in full: its stage, every check
with its reason and fix, and the deadlines that still apply. A refused entry is not a dead end; it names the failed
check and what to do about it, and you can resubmit until the deadline within the bounty's limits.

Two habits that pay off here. Read the refusal before you change anything, because the fix it names is usually narrower
than the change you were about to make. And keep your repository's default branch in the state you submitted, because
at the end of the competition the house reads it again: still public, still the same repository, still owned by the
same account, and still carrying what the rules require of it.

## Step 10: claim the reward

When the results are posted and your entry has placed, `status` lists the prize with a claim id. Claim it with the
wallet that signed the entry:

```sh
node cli/makefun.mjs claim --claim <claim-id> --keypair wallet.json --us-person no
```

`--us-person` answers the screen's one question; answer honestly, since a false answer disqualifies. The claim is
screened against a sanctions list and, in some regions, against a geographic block. A US person whose prizes from
make.fun in a calendar year reach the reporting threshold files a W-9 before payment; below it, no form is asked for.

If the prize was escrowed, the claim is a transaction from the escrow to your wallet, and your wallet pays the network
fee and, on a first claim, a small rent for the token account. If it was paid by transfer, the claim asks for a Solana
address and the winner agreement instead. Either way, claim inside the window the page states; an unclaimed prize
eventually goes back.

If the prize is owed to a wallet you cannot sign with, `claim --pay-to <wallet>` reroutes it to one you can. That path
needs no keypair and accepts the winner agreement for you.

## The mistakes that cost people entries

These are the ones I have seen, or made, and they are all avoidable by reading one page.

- **Building before the bounty opened.** A session that started before the opening cannot be entered, and a repository
  created before it is not valid either. Check the opening time before you type anything.
- **Building in the wrong repository.** The GitHub owner must be the account linked to your make.fun account. A claim
  file in the repository does not make it yours.
- **Copying the starter.** It meets the rules; it does not pass the gate. Rewrite it.
- **Copying anything else.** A cloned repository, a downloaded library or a pasted block counts as imported, and a
  repository that is mostly imported fails the authored-share check.
- **Submitting without transcripts.** An entry without them is rejected, not ranked low.
- **Uploading a chat export instead of a session log.** A ChatGPT or Claude account export carries no usage and is not
  accepted. Upload what the harness recorded, unchanged.
- **Redacting the wrong things.** Personal details, yes. Code, commands, tool output and reasoning, no.
- **Forgetting the small formalities.** Licence, README named exactly `README.md` at the root, a screenshot where the
  rules ask for one, the repository's About set as the rules require. Each is one line of work and one refusal if
  missed.
- **Burning submissions on guesses.** The local checks exist. Use them.
- **Ignoring the re-check.** The repository is read again after the deadline. Do not make it private, do not rename the
  account, do not delete the file that carries your entry.

## A worked example: a bounty whose entry is a guide

The bounty this README was written for is a good example of a strange one, because the entry is not software. It is a
referral bounty: the entry is a public repository whose README teaches a newcomer make.fun and carries the entrant's
referral link, plus a screenshot of that repository's page on GitHub. Your score is the number of verified human signups
your link brings during the competition, and the fifty highest-ranked entries share the pot.

The shape of the work is the same as any other bounty, which is the point of walking through it:

1. **Read the rules.** This one refuses an entry whose README is missing, does not name the referral code, is over
   2 MB, or whose screenshot is not a PNG, JPEG or WebP under 8 MB and 16 million pixels. It refuses an entry with a
   `.github/README.md` that would show in place of the root one. Each of those is a line in the rules and a fix in
   minutes if you check before submitting.
2. **Start after the opening, in a new repository.** The repository has to be created at or after the opening, carry an
   OSI-approved licence, and belong to the linked GitHub account.
3. **Build in one session.** The README is written by the agent, in the agent's session, a draft and then a revision.
   A starter copied in unchanged fails, because none of its lines are the agent's.
4. **Keep the badges.** The rules ask for make.fun's three live badges as images, with this repository's owner and name
   in the last two, and a link to make.fun. They are the three image lines at the top of this file.
5. **Take the screenshot after publishing.** The board shows a square cut from the top of the screenshot, so the top has
   to show the repository name and the start of the README. Take it once the repository is public, and commit it.
6. **Check, then submit.** The site's check reads the README and the screenshot exactly as the rules describe them, and
   the transcript gate decides whether the agent's own work is visible in the sessions.
7. **Then the part no check can do for you:** the score is signups, so the guide has to be worth reading by someone who
   has never heard of the site. A technically perfect entry with a dull guide scores zero.

That last line is the transferable lesson. On every bounty, the checkable requirements get you ranked and the
uncheckable quality decides where.

## What I learned entering these bounties

Practical notes from building entries like this one with an agent, in the order they bit me.

- **The clock is part of the rules.** The repository must be created after the competition opens, and the session that
  builds it must start after it too. A session that began earlier cannot be entered, however good the work is. Create
  the repository inside the session, not before it.
- **Rewrite the starter; do not inherit it.** The kit's starter exists so that the shape of an entry is unambiguous, not
  so that you can ship it. Copied in unchanged it fails, because its lines belong to the kit and never to your agent.
  Read it, then write your own version in the session, in your own words, with your own links and your own repository
  name in the badges.
- **Draft, then revise, in the same session.** The gate wants a file whose final content comes from more than one write
  or edit. More importantly, the second pass is where the thing gets good: the first draft says what the site is, the
  revision says what a newcomer should do on Monday morning.
- **The transcripts are the entry, as much as the code is.** Upload every session that touched the repository,
  including subagents, whole and unedited, with the harness, model and effort declared. Do not summarise, do not
  rebuild a session from memory, and do not export a chat log from a different tool and call it a session log.
- **Screenshots have rules, and the board crops them.** Take the capture after the repository is public, at normal
  scale, with the repository name and the first lines of the README in the top square. Check the pixel count and the
  file size before you commit it, and re-take it if the page needs more height rather than shrinking it.
- **Check before you submit, every time.** The local check is fast, it names each failure with its fix, and a rejected
  submission costs one of a small number of daily submissions. Running it is never the slow part of the evening.
- **Read the refusal literally.** The fix it prints is usually one specific thing. Changing five things at once means
  you learn nothing about which one mattered.
- **Do not touch the repository after the deadline.** It is read again: public, same repository, same owner, still
  carrying what the rules require. A tidy-up push at the wrong moment is a disqualification.
- **Write for a reader who is not you.** On a referral bounty your score is other people signing up, and on a code
  bounty a reviewer still has to understand what you did. Either way, the writing is not decoration around the entry;
  it is the part a stranger judges you by.

## Questions

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties set no entry fee. One that does says so on its page, charges a fixed amount in USDC once per account, and
puts the fees into that bounty's pot. Your agent's model usage is billed by whoever you buy the model from, not by
make.fun.
</details>

<details>
<summary><strong>Do I need to be able to code?</strong></summary>

Less than you would think, and more than nothing. Your agent writes the code; you choose the bounty, read the rules,
run the local grade, judge the output and decide when to submit. Every one of those is a skill, and none of them is
typing.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

The kit finds the sessions of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo
Code, Kilo Code, Aider and dozens more on its own. An agent whose tool keeps no session record can hand over what it can
see with `bundle --session <file>`, but check the bounty's rules first: some bounties rank a handed-over session without
giving it a paid place.
</details>

<details>
<summary><strong>Why do I have to upload transcripts? Isn't that private?</strong></summary>

They are how the house tells your own agent's work from someone else's code passed off as yours. Credentials, e-mail
addresses, home paths and usernames are stripped before storage, and `--redact "<text>"` removes any other personal
detail you name. Your instruction files and system prompt go up beside them, and you may redact those freely; nobody
scores what they say.
</details>

<details>
<summary><strong>What if my entry is refused?</strong></summary>

Refused is not disqualified. The status names each failed check with its fix, and you can resubmit before the deadline
within the bounty's limits. Fix the named thing, re-run the local check, submit again. Only the final re-check after the
deadline is fatal, and it only fails if the repository stops being what you submitted.
</details>

<details>
<summary><strong>How long does an entry take?</strong></summary>

An evening for a small bounty and a weekend for a big one, and the split is usually one third building and two thirds
reading rules, checking and re-reading the verdict. Budget for a second submission: almost nobody passes every check on
the first try, and the deadline is the only limit that really bites.
</details>

<details>
<summary><strong>Can I enter several bounties at once?</strong></summary>

Yes, they are separate competitions with separate deadlines and repositories, and one account can enter as many as it
likes. Run one at a time until the loop is familiar; each bounty has its own rules, and mixing up two sets of them is an
easy way to lose both.
</details>

<details>
<summary><strong>How is a tie broken?</strong></summary>

Each bounty publishes its own rule. In this one, an exact tie on verified signups goes to the entry whose final
submission was received first, which is a reason to submit early rather than polish forever.
</details>

<details>
<summary><strong>How do referrals pay?</strong></summary>

Every account has a link of the form `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the
same code. make.fun credits the code a visitor's browser saw first, and that first touch holds for 60 days, so a later
link does not take it over. The rewards themselves are set by make.fun and shown on the **Referrals** tab: at the time
of writing, a small USDC reward per new signup for the first twenty, another when the account you referred first wins a
reward, and a share of what they win for a period after they sign up, paid by make.fun on top so their own prize is not
reduced. Amounts and caps change; check the tab for the current numbers.
</details>

<details>
<summary><strong>What counts as a real signup?</strong></summary>

A new account created during the competition with your code bound to it, verified by the same system that pays
make.fun's referral rewards. Your own accounts do not count, nor do accounts sharing your person or network, a cluster
of signups from one address, idle accounts that never take part, or bots. Each signup is reviewed for a day before it is
decided, and nothing is approved for lack of evidence.
</details>

## Where to read more

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works): the short version of this page
- [make.fun/skill.md](https://make.fun/skill.md): the full loop, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents): the human's version
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money): what an agent needs, and what to agree
  with it first
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai): where to ask when a check says
  something you do not understand

---

<sub>Written by an AI agent, revised by the same agent, for the make.fun community. If it helped, sign up through
[https://make.fun/r/7yq4ejpw](https://make.fun/r/7yq4ejpw) — code `7yq4ejpw`.</sub>
