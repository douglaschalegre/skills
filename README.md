# Skills

My reusable agent skills, starting with selected skills from `~/.agents/skills`.

## Available skills

| Skill | Purpose |
| --- | --- |
| [tell-the-story-of-changes](tell-the-story-of-changes/SKILL.md) | Write compact pull request descriptions in Brazilian Portuguese using a fixed template. |
| [summon-a-review](summon-a-review/SKILL.md) | Open pull requests against the source branch, assign yourself, and write the body with tell-the-story-of-changes. |
| [cast-review-remarks](cast-review-remarks/SKILL.md) | Add pull request review comments and reply to review threads with context from the code. |
| [make-bugs-confess](make-bugs-confess/SKILL.md) | Investigate bugs in waves, test a simple fix, and compare it with an independent how and why analysis. |

## Install a skill

Install with the [skills CLI](https://skills.sh/docs):

```sh
npx skills add douglaschalegre/skills --skill tell-the-story-of-changes
npx skills add douglaschalegre/skills --skill summon-a-review
npx skills add douglaschalegre/skills --skill cast-review-remarks
npx skills add douglaschalegre/skills --skill make-bugs-confess
```

Or install manually.

Clone this repository:

```sh
git clone https://github.com/douglaschalegre/skills.git
```

Copy the skill into your local skills directory:

```sh
mkdir -p ~/.agents/skills
cp -R skills/tell-the-story-of-changes ~/.agents/skills/
cp -R skills/summon-a-review ~/.agents/skills/
cp -R skills/cast-review-remarks ~/.agents/skills/
cp -R skills/make-bugs-confess ~/.agents/skills/
```

`summon-a-review` requires `tell-the-story-of-changes`. Install both to use the full workflow.

`make-bugs-confess` requires `principle-subtract-before-you-add`, `how`, and `why`, plus support for independent agents. These dependencies are not bundled in this repository.

If a skill is already installed, back it up before replacing it.

## Add a skill

Place each skill in `<skill-name>/` at the repository root, including its `SKILL.md` and any supporting files. Add it to the table above.
