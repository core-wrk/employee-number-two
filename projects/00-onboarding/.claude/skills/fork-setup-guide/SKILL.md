# Skill: Fork Setup Guide

## Role

You actively guide the founder through forking the repo, making their fork private, and completing an initial commit. You verify each step before moving to the next. This is a procedural skill — you walk them through it, not just describe it.

## Behavior

**Step-by-step, verified.** Do not give the founder all the instructions at once. Walk through one step, verify it worked, then move to the next. If something goes wrong, troubleshoot before continuing.

**Tone.** Direct and helpful. This is a setup task, not a deep conversation. Be efficient but not terse — explain *why* each step matters when it is not obvious.

## Flow

### Step 1: Check Current State

Run `git remote -v` to see where the repo is currently pointed.

**If origin points to the upstream repo** (`core-wrk/employee-number-two` or the maintainer's repo):
- The founder has cloned the upstream repo directly. They need to fork first.
- Explain: "You have cloned the original repo directly. To keep your work private and separate, you need to create your own fork on GitHub. Let me walk you through that."
- Proceed to Step 2.

**If origin points to the founder's own GitHub account:**
- The founder has already forked. Verify the fork looks correct.
- Skip to Step 4.

**If no remotes are configured:**
- Unusual. Ask the founder how they got the repo and help them set up remotes correctly.

### Step 2: Guide Fork Creation

Since Claude Code cannot create GitHub forks directly, instruct the founder:

1. "Go to the Employee Number Two repo on GitHub"
2. "Click the **Fork** button in the top right"
3. "Make sure to select your own account as the destination"
4. "Once the fork is created, copy the URL of your fork"

Wait for the founder to confirm they have completed this and provide their fork URL.

### Step 3: Update Remotes

Once the founder has their fork URL:

1. Rename the current origin to upstream: `git remote rename origin upstream`
2. Add their fork as origin: `git remote add origin <founder-fork-url>`
3. Run `git remote -v` to verify:
   - `origin` should point to the founder's fork
   - `upstream` should point to the original repo

Show the output and confirm it looks correct.

### Step 4: Verify Fork Privacy

Ask the founder: "Is your fork set to **Private** on GitHub? This is important — your founder profile, startup hypothesis, and all outputs contain proprietary information about your startup. If your fork is public, anyone can see it."

If they are unsure, guide them:
1. "Go to your fork on GitHub"
2. "Click **Settings** → **General**"
3. "Scroll to the **Danger Zone** section"
4. "Click **Change repository visibility** and set it to Private"

Do not proceed until the founder confirms the fork is private.

### Step 5: Initial Commit

Guide the founder through an initial commit to confirm everything is working:

1. Check if there are any changes to commit with `git status`
2. If there are changes (there may not be in a fresh fork): stage and commit them
3. Push to their fork: `git push -u origin main`
4. Verify with `git log --oneline -1` that the commit exists

### Step 6: Confirm Setup

Summarize what was done:
- Fork created and set as origin
- Upstream repo preserved as a remote (for pulling future updates)
- Fork is private
- Initial push confirmed

Tell the founder: "Your fork is set up. Everything you create in this repo — your founder profile, hypothesis, research, and outputs — will be committed to your private fork. The upstream repo stays clean."

## Edge Cases

**Founder is working in a GitHub Codespace:** Codespaces are automatically tied to a repo. Ask if the Codespace is running on their fork or the upstream repo. If upstream, they should create a fork first and then either create a new Codespace from their fork or update the remote configuration.

**Founder wants to keep the fork public:** Warn them that global context files and outputs contain proprietary startup information. If they still want to keep it public, respect the decision but recommend they add `global/context/` and `projects/*/outputs/` to their `.gitignore` (which should already be configured).

**Founder already has commits on the upstream clone:** Help them preserve their work by pushing to a branch on their new fork before switching remotes.

## What Not To Do

- Do not dump all instructions at once
- Do not skip the privacy verification step
- Do not proceed past a failed step without troubleshooting
- Do not assume the founder knows how GitHub forks work — explain briefly if needed
