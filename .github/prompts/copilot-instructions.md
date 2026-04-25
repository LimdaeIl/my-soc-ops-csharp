# Soc Ops – Copilot Workspace Instructions

**Soc Ops** is a Social Bingo game built with **Blazor WebAssembly (.NET 10)** for in-person team building events. Find people who match questions, mark squares, and get 5 in a row to win. This workspace is designed for AI-assisted development with specialized instructions for frontend work and a 5-part learning lab.

---

## Quick Start

```bash
# Build
cd SocOps && dotnet build

# Run dev server (http://localhost:5166)
cd SocOps && dotnet run

# Run tests (when applicable)
dotnet test
```

---

## Architecture & File Structure

```
SocOps/
├── Components/          # Reusable Blazor components
│   ├── GameScreen.razor     # Main game board display
│   ├── StartScreen.razor    # Welcome & setup screen
│   ├── BingoBoard.razor     # Grid manager & win detection
│   ├── BingoSquare.razor    # Individual clickable square
│   └── BingoModal.razor     # Modal dialogs (rules, etc.)
├── Services/            # Business logic & state management
│   ├── BingoGameService.cs     # State & event coordination
│   └── BingoLogicService.cs    # Win detection, game rules
├── Models/              # C# data models
│   ├── GameState.cs        # Game state serialization
│   ├── BingoSquareData.cs  # Square data & metadata
│   └── BingoLine.cs        # Win line validation
├── Data/                # Static data
│   └── Questions.cs        # Bingo questions & prompts
├── Layout/              # Global layout components
│   ├── MainLayout.razor
│   ├── MainLayout.razor.css
│   ├── NavMenu.razor
│   └── NavMenu.razor.css
├── Pages/               # Routable pages
│   ├── Home.razor       # Game container
│   ├── Counter.razor    # Example page
│   ├── Weather.razor    # Example page
│   └── NotFound.razor   # 404 handler
└── wwwroot/             # Static assets
    ├── css/
    │   └── app.css          # Custom utility classes (see css-utilities.instructions.md)
    ├── index.html
    └── lib/                 # Bootstrap & dependencies
```

---

## Development Conventions

### C# & Blazor

- **Naming**: PascalCase for public members, camelCase for private/parameters
- **Nullability**: Enabled (`<Nullable>enable</Nullable>` in .csproj)
- **Usings**: Implicit (via `<ImplicitUsings>enable</ImplicitUsings>`)
- **Components**: Use `@inherits`, `@code` blocks; event handlers as `async Task` methods
- **State**: Managed via `BingoGameService` with event-driven updates
- **JSInterop**: Used for localStorage persistence; consider abstracting into services

### Styling

- **Framework**: Custom CSS utilities in `wwwroot/css/app.css` (Tailwind-like approach)
- **Colors**: Defined as CSS variables (e.g., `--color-accent`, `--color-marked`)
- **Responsive**: Mobile-first using flexbox/grid utilities
- **See**: [CSS Utilities Instructions](.github/instructions/css-utilities.instructions.md)

### Frontend Design

When redesigning UI or building new components:
- **Avoid generic aesthetics**: Use distinctive typography, cohesive color themes, and purposeful motion
- **Maximize impact**: Orchestrate animations for high-impact moments (page load, win states)
- **Think creatively**: Reference the context (team building, social themes) for design inspiration
- **See**: [Frontend Design Instructions](.github/instructions/frontend-design.instructions.md)

---

## Development Checklist

Before committing any changes:

- [ ] `dotnet build SocOps/SocOps.csproj` passes with no errors
- [ ] No unused variables, imports, or dead code
- [ ] CSS utilities are used consistently (avoid inline styles)
- [ ] Blazor components follow single-responsibility principle
- [ ] State changes trigger `OnStateChanged` events in `BingoGameService`
- [ ] New features are testable (logic isolated in Services)

---

## Learning & Workshop Structure

This workspace includes a **5-part learning lab** in the `workshop/` folder. Each part covers key concepts and includes hands-on tasks using Copilot agents:

| Part | Title | Focus Area |
|------|-------|-----------|
| **00** | [Overview & Checklist](../workshop/00-overview.md) | Prerequisites & project setup |
| **01** | [Setup & Context Engineering](../workshop/01-setup.md) | Workspace instructions, agents, prompts |
| **02** | [Design-First Frontend](../workshop/02-design.md) | UI redesign with Plan Mode & CSS refinement |
| **03** | [Custom Quiz Master](../workshop/03-quiz-master.md) | Generative agents for custom themes |
| **04** | [Multi-Agent Development](../workshop/04-multi-agent.md) | TDD & design patterns with specialized agents |

**Recommended workflow**: Follow the numbered parts sequentially. Each builds on prior context and introduces new agent capabilities.

---

## Specialized Instructions

This workspace includes focused instruction files for specific tasks:

### Frontend Design
📄 [.github/instructions/frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md)

Use when designing or building new UI components. Emphasizes creative, distinctive aesthetics over generic "AI slop" patterns.

**Trigger**: "Design/build web components", "redesign the UI", "create a new theme"

### CSS Utilities
📄 [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md)

Reference guide for available CSS utility classes. Use when styling components or creating layouts.

---

## Common Workflows

### Add a New Game Feature

1. **Define state** in `SocOps/Models/` (e.g., `NewFeature.cs`)
2. **Add logic** in `SocOps/Services/BingoLogicService.cs`
3. **Expose state** via `BingoGameService` with an `event` for changes
4. **Create component** in `SocOps/Components/` (inherit from `ComponentBase`)
5. **Integrate** into `GameScreen.razor` or create a new page
6. **Style** using CSS utilities from `wwwroot/css/app.css`
7. **Build & test**: `dotnet build && dotnet run`

### Implement a Custom Quiz Theme

Use the **Quiz Master agent** (Part 03 of the lab) to generate:
- New question sets with custom branding
- Theme-specific styling (colors, fonts, animations)
- Component variations (e.g., dark mode, compact layout)

See [03-quiz-master.md](../workshop/03-quiz-master.md) for detailed instructions.

### Refactor or Optimize Components

Use **code review agents** (Part 04 of the lab):
- **Scavenger Hunt mode**: TDD-style refactoring (Red → Green → Refactor)
- **Code quality patterns**: Service isolation, testability, separation of concerns

---

## Environment & Tools

- **Framework**: .NET 10 SDK (Blazor WebAssembly)
- **Language**: C# 13 (with nullable reference types enabled)
- **Styling**: Custom CSS utilities + Bootstrap (in `wwwroot/lib/`)
- **Dev Server**: Listens on `http://localhost:5166`
- **State**: Persisted via browser localStorage
- **Deployment**: GitHub Pages (automatic on push to `main`)

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Build fails | Run `dotnet clean` then `dotnet build SocOps/SocOps.csproj` |
| Dev server won't start | Check port 5166 is available; verify launchSettings.json exists |
| Components not updating | Ensure `StateHasChanged()` is called after state changes |
| CSS not applied | Verify class names match `wwwroot/css/app.css` and are used in components |
| localStorage errors | Check browser DevTools → Application tab for quota/permissions issues |

---

## Integration with Copilot Agents

This workspace is designed to work with Copilot agents via prompts and specialized instructions:

- **`/setup`** prompt: Initial workspace bootstrap and verification
- **Frontend design instruction**: Triggered for UI/UX tasks
- **CSS utilities instruction**: Referenced for styling questions
- **Part-based prompts**: In `workshop/` for guided learning

To invoke an agent: Type `/` in Copilot chat and select the relevant prompt or instruction.

---

## Resources

- 📖 **Lab Guide**: [workshop/GUIDE.md](../workshop/GUIDE.md)
- 🎮 **Live Demo**: https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/
- 📚 **Official Docs**: [Blazor WebAssembly](https://learn.microsoft.com/en-us/aspnet/core/blazor/webassembly)
- 🐙 **Contributing**: See [CONTRIBUTING.md](../CONTRIBUTING.md) (Microsoft CLA required)

---

**Last updated**: April 2026  
**Maintained by**: Soc Ops Development Team
