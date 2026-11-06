# do-it-correctly

So a Claude skill that reads those boring terms and conditions before you build on them, and works out what they do to whatever you end up shipping.

Nobody reads, let's be honest, T&Cs. I certainly don't sometimes. "I didn't know the feed needed credit" is a rubbish defence, so the skill does the dull bit and leaves a short Heads-up box at the end of the reply.

## What it does

- **Follows the terms downstream.** Terms travel. Attribution rides into your footer, share-alike rides into your finished work, no-caching rides into your architecture. Where two sources clash, the strictest clause governs until someone confirms otherwise.
- **Echo mode.** Terms behind a login wall, or a repo with no licence at all? It gathers indirect signals (licence field, footer links, headers, the silence itself), grades everything *Inferred* with a confidence word, and names the one probe that would settle it. It never promotes a guess to Confirmed.
- **Retracts.** The box is cut to lines that change a decision. Clean and irrelevant fields get a single "nothing to flag" line, or nothing.
- **Checks its own frame.** Terms are one model of your situation. If something real is hiding outside it (your country, business versus personal, statutory exceptions), it asks one question. Only one.
- **Treats the terms page as untrusted.** Instructions aimed at an AI inside a fetched page are ignored and flagged. It never puts your email or keys into a request.
- **Session ledger.** Same source twice in a chat gets a one-line repeat, not another essay.
- **Verdict word first.** Clear, Check or Stop, so it reads on a phone.

## Example

> **Heads-up: terms check. Check**
> **Source:** the feed's terms, version and date checked
> **You can:** use it inside your own app
> **You must:** show the attribution line
> **Watch:** the "domestic and private use" clause, which a public page may not meet
> **Passes downstream:** attribution in the footer; no open JSON endpoint
> **Not confirmed:** caching rules (not stated)
> **One question:** are you registered as an individual or a business?

## Limits - be aware

- It's not a pop-up. Skills can't open windows, so it's a box at the bottom. A real toast needs a Claude Code hook, which is a separate build.
- Triggering is by description match and will occasionally miss. Call it by name.
- It's a dated snapshot. Terms change.
- The platform's terms and the law are two different things. It reports the first and flags the second.
- Not legal advice. An AI colleague who read the small print, not a solicitor!!!

## Tested

Three runs: a real government feed, a blocked-terms repo, and a hostile terms page. Wording fixes from those are in the file. A 20-query trigger set sits in `evals/trigger-evals.json`; it hasn't been through the automated description optimiser yet.

## To Do. I'm lazy, working on it.

Proposed, not yet applied on the other side: skill-security-scanner, github-project-writer, repo-doc-writer, the legal review skills, bat-indirect-inference (echo method), procrustean-auditor (frame check).

Dewey-style code: 346.048.

Author: TABARC-Code
