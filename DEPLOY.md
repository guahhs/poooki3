# Deploying this skill

Four paths. Pick by who is installing it, not by which is most impressive.

Before any of them: three files contain the literal text
`REPLACE WITH YOUR NAME` — `LICENSE`, `.claude-plugin/plugin.json`, and
`.claude-plugin/marketplace.json` (which also has
`REPLACE-WITH-YOUR-GITHUB-USERNAME`). Replace them first.

---

## 1. You, on this machine — already done

The skill is installed at:

```
C:\Users\ACER\.claude\skills\application-essay-studio\
```

A personal skill there is available in every Claude Code session on this
machine, in every directory, with no further action. Nothing to deploy.

To update it, edit the files in place. To remove it, delete the folder.

---

## 2. You, in claude.ai and Cowork — upload the zip

Use `application-essay-studio.skill.zip` in this folder.

1. Go to `claude.ai/customize/skills`
2. Upload the zip
3. It becomes available in chat and Cowork on your account

The archive is already built correctly: the skill folder is the top-level entry
(`application-essay-studio/SKILL.md`, not a bare `SKILL.md`), and entry names
use forward slashes. Both matter — a zip of the folder's *contents* rather than
the folder is rejected, and Windows' built-in `Compress-Archive` writes
backslashes that non-Windows extractors mishandle, so rebuild with the same
method if you ever repackage.

**Constraint:** the upload accepts exactly one `SKILL.md`. This skill has one,
with everything else under `references/`, so it uploads cleanly. Do not add a
second `SKILL.md` anywhere in the tree — only Claude Code's filesystem loader
tolerates nested ones.

**Caveat:** web access in claude.ai depends on your account and admin settings.
Where it is unavailable, the accuracy pass reports `unverified` rather than
guessing. That is by design, but it means the highest-value check — verifying
the essay's claims against the programme's published curriculum — may not run.

---

## 3. A specific project or a shared repo — project-scoped skill

Copy `skills/application-essay-studio/` to `.claude/skills/` inside the
repository. Anyone who clones it and opens Claude Code there gets the skill
automatically, with no install step.

Good when a group of applicants shares one working repository. No marketplace,
no versioning, no review.

---

## 4. Other people — GitHub plugin marketplace

This is the real "give it to my students" path. **`git` is not installed on
this machine**, so install it first from `git-scm.com`, or create the repository
through GitHub's web interface and upload this folder's contents.

Once you have git:

```bash
cd C:\Users\ACER\Documents\aes-plugin
```

```bash
git init -b main
```

```bash
git add . && git commit -m "Application Essay Studio v1.0.0"
```

Create an empty repo named `aes-plugin` on GitHub, then:

```bash
git remote add origin https://github.com/YOUR-USERNAME/aes-plugin.git
```

```bash
git push -u origin main
```

Your students then run, in Claude Code:

```
/plugin marketplace add YOUR-USERNAME/aes-plugin
```

```
/plugin install application-essay-studio@application-essay-studio
```

Alternatively, at the account level: `claude.ai/customize/plugins` has
**Add marketplace** and **Upload plugin**. One add there propagates to chat,
Cowork and Claude Code as a `@synced` plugin — convenient for students who
don't use a terminal. Note this requires a paid plan; it is not on Free.

### Things to tell your students

- **A plugin can run arbitrary code with their user privileges.** This one is
  skills-only — no hooks, no MCP servers, no `bin/`, nothing but Markdown — so
  it sits near the floor of risk. They can verify that themselves: the whole
  plugin is seven `.md` files plus two JSON manifests. Encourage the check; it
  is the right habit.
- **Anthropic does not review this.** Review covers plugins listed in the
  official directory only, and explicitly not plugins added from a marketplace
  URL or uploaded directly. The pre-install warning text looks identical either
  way, so it will not tell them apart.
- **Auto-update is off for third-party plugins.** They will need to re-run
  `/plugin marketplace update` to get your fixes. Tell them when you ship one.
- **Uninstalling leaves a cache for about 14 days.**
- **Cloud sessions have no plugin support at all**, including `claude.ai/code`.
  The marketplace route works in the desktop app and the CLI.

### If you want it in the official directory

Submission puts it through automated validation, a security scan and human
review of the listing, and makes it installable without a marketplace URL.
Worth it only if you want strangers using it. Note that 14 marketplace names
are reserved for Anthropic, and Claude Code refuses them unless the source is
`github.com/anthropics/`.

---

## 5. Programmatic use — the Skills API

For running this inside your own application rather than in Claude Code.

Upload the skill via the Files API and reference it in a request with these
beta headers:

```
anthropic-beta: skills-2025-10-02,code-execution-2025-08-25,files-api-2025-04-14
```

Constraints: one top-level `SKILL.md`, under 8 MB, at most 8 skills per
request. Not available on Amazon Bedrock or Google Vertex.

**The significant one:** the API's skill container has **no network access and
no runtime package installation.** Passes 1, 3, 4 and 5 work normally. Pass 2 —
the four-layer accuracy check and the programme-claim verification, which is the
single highest-leverage thing this skill does — cannot run. It will report
`unverified` as designed, but you are deploying a materially weaker tool. If
accuracy checking matters to you, deploy to Claude Code instead, which has full
network access.

---

## Updating after a change

The installed skill, the bundle, and the zip are three separate copies. After
editing the installed skill at `~/.claude/skills/application-essay-studio\`:

```powershell
Copy-Item -Force "C:\Users\ACER\.claude\skills\application-essay-studio\SKILL.md" "C:\Users\ACER\Documents\aes-plugin\skills\application-essay-studio\SKILL.md"; Copy-Item -Force "C:\Users\ACER\.claude\skills\application-essay-studio\references\*.md" "C:\Users\ACER\Documents\aes-plugin\skills\application-essay-studio\references\"
```

Then bump `version` in both JSON manifests, rebuild the zip, and push.

## Version history

**1.0.0** — first release. Includes four fixes made after a blind recall test
against an expert reviewer's own markup: cap-versus-range word limits (a range
has a floor, and falling below it is a hard defect), the findings budget applied
to structural findings only with corrections exempt, a noun-and-number sweep as
Pass 5, and a remembered statistic removed from `references/fact-check.md`.
