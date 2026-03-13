# Copilot Workspace Instructions

## Mandatory Pre-Commit Checklist

> Run these before every commit  do not skip.

```bash
dotnet build SocOps/SocOps.csproj   # must have 0 errors, 0 warnings
dotnet format SocOps/SocOps.csproj  # lint  fix all style violations
dotnet test                          # all tests must pass (when present)
```

- [ ] `dotnet build`  no errors or warnings
- [ ] `dotnet format`  no lint violations
- [ ] `dotnet test`  all tests pass
- [ ] No unused `@using` directives or variables
- [ ] New CSS classes added to `app.css` (no inline styles, no Bootstrap)

---

## Project

**Soc Ops**  Social Bingo on Blazor WebAssembly (.NET 10). Players mark squares by finding people who match questions; first to 5-in-a-row wins.
Dev server: `dotnet run --project SocOps/SocOps.csproj`  http://localhost:5166

---

## Architecture

```
SocOps/
 Components/   BingoBoard, BingoSquare, BingoModal, GameScreen, StartScreen
 Models/       BingoSquareData, BingoLine, GameState (enum: Start|Playing|Bingo)
 Services/     BingoGameService (state + localStorage)  BingoLogicService (static: board gen, toggle, win check)
 Data/         Questions.cs  question bank (must have 25 entries)
 Pages/        Home.razor  root page
 wwwroot/css/  app.css  all utility classes
```

---

## Conventions

- PascalCase public members; `_camelCase` private fields
- State mutations  always through `BingoGameService`, always call `NotifyStateChanged()`
- localStorage saves: `_ = SaveGameStateAsync();`  fire-and-forget, never await in click handlers
- Logic in `.razor @code` blocks or Services; no `.razor.cs` split files
- Register services as `Scoped` in `Program.cs`
- Use `EventCallback` for childparent events

---

## Styling

Custom Tailwind-like utilities in `app.css`  see `.github/instructions/css-utilities.instructions.md`.

| | Examples |
|---|---|
| Layout | `.flex`, `.flex-col`, `.grid`, `.grid-cols-5`, `.items-center` |
| Spacing | `.p-1``.p-6`, `.mb-2``.mb-8`, `.gap-1`, `.mx-auto` |
| Color | `.bg-accent` (blue), `.bg-marked` (green), `.bg-gray-50/100` |
| Type | `.text-xs``.text-5xl`, `.font-semibold`, `.font-bold` |
| Misc | `.rounded-lg`, `.shadow-xl`, `.transition-all`, `.duration-150` |

---

## Agents & Prompts

| | File | Purpose |
|---|---|---|
| Agent | `quiz-master.agent.md` | Generate/manage question sets |
| Agent | `pixel-jam.agent.md` | Creative UI overhaul |
| Agent | `ui-review.agent.md` | Styling & accessibility review |
| Agent | `tdd.agent.md` | Full TDD cycle (red/green/refactor) |
| Prompt | `setup.prompt.md` | Bootstrap local dev |
| Prompt | `cloud-explore.prompt.md` | Cloud deployment options |

---

## Pitfalls

- **No Bootstrap**  `wwwroot/lib/bootstrap/` exists but is not imported; use `app.css` utilities only
- **No `await` on localStorage**  fire-and-forget is intentional
- **Board is always 55**  `BingoLogicService` hardcodes 25 squares
- **`BingoLogicService` is static**  no DI constructor; all methods are static helpers
