# persona

Toggleable reply-tone personas for [pi](https://github.com/badlogic/pi-mono) (pi-coding-agent).

A single-file extension (`persona.ts`) that applies a persona to the assistant's
**tone** via the system prompt. Personas affect voice only — a shared
`HARD RULES` block keeps all technical substance (code, commands, file paths,
error messages, explanations) exact and complete.

Off by default. State persists per session and is restored on session resume.

## Install

Copy `persona.ts` into your pi extensions directory:

```sh
cp persona.ts ~/.pi/agent/extensions/
```

Restart pi (or reload extensions).

## Usage

| Command | Effect |
| --- | --- |
| `/persona` | Show status + available personas |
| `/persona list` | List personas |
| `/persona <id>` | Activate a persona (e.g. `/persona pirate`) |
| `/persona toggle` | Toggle current persona on/off (remembers last used) |
| `/persona random` | Activate a random persona |
| `/persona off` | Deactivate |

A `🎭` status indicator appears while a persona is active.

## Built-in personas

Scheming Eunuch · Pirate Captain · Drill Sergeant · Noir Detective · Mad
Scientist · Victorian Butler · Caveman · Sir Humphrey (Bureaucrat) · Nature
Narrator · Tyrant Chef · Yoda · The Bard · Conspiracy Theorist · … (see
`PERSONAS` in `persona.ts`)

## Adding a persona

Append an entry to the `PERSONAS` array in `persona.ts`:

```ts
{
	id: "my-persona",
	name: "My Persona",
	blurb: "One-line description",
	prompt: `You are now speaking as ... (tone instructions only)`,
},
```

No other changes needed.

## Guarantees

Every persona is followed by a `HARD RULES` block that:

- keeps technical substance exact and complete;
- makes precision win over persona in any conflict;
- drops the act for safety warnings, destructive-action confirmations, and
  anything genuinely serious;
- never refuses, delays, or degrades a task because of the persona.
