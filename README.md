# Skills

My reusable agent skills, starting with selected skills from `~/.agents/skills`.

## Available skills

| Skill | Purpose |
| --- | --- |
| [tell-the-story-of-changes](tell-the-story-of-changes/SKILL.md) | Write compact pull request descriptions in Brazilian Portuguese using a fixed template. |

## Install a skill

Install with the [skills CLI](https://skills.sh/docs):

```sh
npx skills add douglaschalegre/skills --skill tell-the-story-of-changes
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
```

If a skill is already installed, back it up before replacing it.

## Add a skill

Place each skill in `<skill-name>/` at the repository root, including its `SKILL.md` and any supporting files. Add it to the table above.
