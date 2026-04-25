# Soc Ops – Workspace Instructions

🎮 **Soc Ops** is a Blazor WebAssembly (.NET 10) Social Bingo game for team building. Find people matching questions, mark squares, get 5 in a row to win.

---

## 🚨 MANDATORY PRE-COMMIT CHECKLIST

Before committing any changes:

```bash
# 1. Build
dotnet build SocOps/SocOps.csproj

# 2. Run locally (optional but recommended)
cd SocOps && dotnet run

# 3. Code quality checks
- No unused variables, imports, or dead code
- CSS utilities composed (no inline styles)
- Blazor components follow single-responsibility
- State changes trigger BingoGameService events
```

**Commit only when all checks pass.** Failed builds block deployment to GitHub Pages.

---

## Architecture Overview

```
SocOps/
├── Components/          # Blazor UI (*.razor files)
│   ├── GameScreen, StartScreen, BingoBoard, BingoSquare, BingoModal
├── Services/            # Business logic
│   ├── BingoGameService (state + events)
│   ├── BingoLogicService (game rules)
├── Models/              # Data: GameState, BingoSquareData, BingoLine
├── Data/                # Questions.cs (quiz content)
├── Pages/               # Routable pages (Home.razor)
├── Layout/              # MainLayout, NavMenu + CSS
└── wwwroot/css/app.css  # Custom Tailwind-like utilities
```

---

## Development Conventions

| Aspect | Rule |
|--------|------|
| **C# Naming** | PascalCase public, camelCase private |
| **Styling** | Use CSS utilities (app.css); compose, don't inline |
| **Components** | Inherit `ComponentBase`; use `@code` blocks; event handlers as `async Task` |
| **State** | Managed via `BingoGameService`; changes fire `OnStateChanged` event |
| **Responsive** | Mobile-first; test at 320px, 768px, 1200px |

---

## Quick Commands

```bash
cd SocOps

# Build
dotnet build SocOps.csproj

# Run dev server (http://localhost:5166)
dotnet run

# Tests (when applicable)
dotnet test
```

---

## Specialized Instructions

### Frontend Design
📄 **Use when**: Designing/refactoring Blazor components, creating themed screens, adding animations
- Activates on: `**/Components/**/*.razor`
- Focus: Distinctive aesthetics, creative palettes, high-impact animations

### CSS Utilities
📄 **Use when**: Styling components, creating layouts
- Reference: Custom Tailwind-like classes in `wwwroot/css/app.css`
- Best practice: Compose utilities; avoid inline styles

---

## Workshop Lab Structure

5-part learning lab in `workshop/` folder:

| Part | Title | Focus |
|------|-------|-------|
| **00** | Overview | Prerequisites & checklist |
| **01** | Setup & Context | Workspace instructions, agents |
| **02** | Design-First | UI redesign with Plan Mode |
| **03** | Quiz Master | Custom quiz themes |
| **04** | Multi-Agent | TDD & code patterns |

---

## Common Workflows

### Add Game Feature
1. Define state in `Models/`
2. Add logic in `Services/BingoLogicService.cs`
3. Expose via `BingoGameService` with event
4. Create component in `Components/`
5. Integrate into `GameScreen.razor`
6. Style with CSS utilities
7. Build & test: `dotnet build && dotnet run`

### Implement Custom Quiz Theme
Use **Quiz Master agent** (Part 03) to generate question sets + themed CSS

### Refactor & Optimize
Use **code review agents** (Part 04) for TDD-style refactoring

---

## Environment

- **Framework**: .NET 10 SDK (Blazor WebAssembly)
- **Language**: C# 13 (nullable refs enabled)
- **Dev Server**: `http://localhost:5166`
- **Deployment**: GitHub Pages (auto on push to `main`)

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Build fails | `dotnet clean` then rebuild |
| Dev server won't start | Check port 5166; verify launchSettings.json |
| Components not updating | Call `StateHasChanged()` after state changes |
| CSS not applied | Verify class names match `app.css` |
| localStorage errors | Check browser DevTools → Application |

---

## Resources

- 📖 Lab Guide: [workshop/GUIDE.md](../workshop/GUIDE.md)
- 🎮 Live Demo: https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/
- 📚 Blazor Docs: https://learn.microsoft.com/en-us/aspnet/core/blazor/
- 🐙 Contributing: [CONTRIBUTING.md](../CONTRIBUTING.md) (Microsoft CLA required)

---

**Last updated**: April 2026
