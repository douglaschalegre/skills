# Skills

My reusable agent skills, starting with selected skills from `~/.agents/skills`.

## Available skills

| Skill | Purpose |
| --- | --- |
| [pr-description](skills/pr-description/SKILL.md) | Write compact pull request descriptions in Brazilian Portuguese using a fixed template. |

## Install a skill

Clone this repository:

```sh
git clone https://github.com/douglaschalegre/skills.git
```

Copy the skill into your local skills directory:

```sh
mkdir -p ~/.agents/skills
cp -R skills/skills/pr-description ~/.agents/skills/
```

If `pr-description` is already installed, back it up before replacing it.

## Add a skill

Place each skill in `skills/<skill-name>/`, including its `SKILL.md` and any supporting files. Add it to the table above.
