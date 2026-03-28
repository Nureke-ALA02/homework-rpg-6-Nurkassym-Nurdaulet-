# AGENTS.md — Repository Guide

## Project Structure

```
homework-rpg-6/
├── src/com/narxoz/rpg/
│   ├── Main.java                       Entry point
│   ├── command/
│   │   ├── ActionCommand.java          Command interface (fully provided)
│   │   ├── AttackCommand.java          Concrete command — student implements execute/undo
│   │   ├── HealCommand.java            Concrete command — student implements execute/undo
│   │   ├── DefendCommand.java          Concrete command — student implements execute/undo
│   │   └── ActionQueue.java            Invoker — student implements all methods
│   ├── chain/
│   │   ├── DefenseHandler.java         Abstract handler — setNext/passToNext provided
│   │   ├── DodgeHandler.java           Concrete handler — student implements handle()
│   │   ├── BlockHandler.java           Concrete handler — student implements handle()
│   │   ├── ArmorHandler.java           Concrete handler — student implements handle()
│   │   └── HpHandler.java              Terminal handler — student implements handle()
│   ├── arena/
│   │   ├── ArenaFighter.java           Hero — student implements mutation methods
│   │   ├── ArenaOpponent.java          Enemy — fully provided
│   │   └── TournamentResult.java       Result POJO — fully provided
│   ├── tournament/
│   │   └── TournamentEngine.java       Engine — student implements runTournament()
│   └── hints/
│       ├── COMMAND_HINTS.md
│       └── CHAIN_HINTS.md
└── out/                                Compiled .class files (gitignored)
```

## Build Commands

Compile all sources (PowerShell, run from project root):

```powershell
javac -d out (Get-ChildItem -Recurse -Filter *.java src | ForEach-Object { $_.FullName })
```

Run:

```powershell
java -cp out com.narxoz.rpg.Main
```

Check git status:

```powershell
git status --short
```

## Coding Style

- **Indentation**: 4 spaces, no tabs
- **Class names**: `PascalCase` (e.g., `DefenseHandler`, `AttackCommand`)
- **Method/field names**: `camelCase` (e.g., `getAttackPower`, `damageDealt`)
- **Constants**: `UPPER_SNAKE_CASE`
- **Package root**: `com.narxoz.rpg`
- **No Javadoc** on methods or fields — design intent goes in TODO comments
- **TODO format**: `// TODO: [specific action or design question]`
- All skeleton methods must compile before students fill them (stubs return `null`, `0`, `"TODO"`, etc.)

## Testing

No test framework is used. Minimum verification is:

1. Project compiles without errors.
2. `Main.java` runs without exceptions.
3. The three demo sections produce readable output (queue, chain, tournament).

## Commit Format

Use conventional commits:

```
feat(chain): implement DodgeHandler
feat(command): implement ActionQueue.executeAll
fix(arena): clamp health in takeDamage
```

## Contributor Notes

- Do **not** commit the `out/` directory.
- Do **not** change `TournamentResult.java` or `ArenaOpponent.java` — they are provided complete.
- Do **not** change `ActionCommand.java` — it is the fixed contract.
- When updating requirements, keep `ASSIGNMENT.md`, `STUDENT_CHECKLIST.md`, and source file TODOs in sync.
