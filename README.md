🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

# 🎮 Soc Ops – Social Bingo for Team Building

Turn boring mixers into engaging experiences! **Soc Ops** is an interactive Social Bingo game where your team finds people who match fun questions and race to get 5 in a row. Built with **Blazor WebAssembly** for instant responsiveness and no server complexity.

**🚀 [Play Now](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/)** • **📚 [5-Part Learning Lab](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/)**

---

## ✨ Why Soc Ops?

- **Zero Setup**: Works instantly in the browser – no apps to install
- **Customizable Questions**: Create themed quizzes for your event (Tech, Culture, Office, Travel, etc.)
- **Responsive Design**: Works on phones, tablets, and desktops
- **Interactive Learning**: Built as an AI-assisted development lab for Copilot users

---

## 🎯 How to Play

1. **Browse questions** on the 5×5 bingo board
2. **Find people** in the room who match each question  
3. **Tap squares** when you find a match
4. **Get 5 in a row** horizontally, vertically, or diagonally to win! 🏆

---

## 🚀 Quick Start

### Prerequisites
- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or higher

### Run Locally

```bash
# Clone the repo
git clone https://github.com/LimdaeIl/my-soc-ops-csharp.git
cd my-soc-ops-csharp

# Start the dev server
cd SocOps
dotnet run

# Open in browser
# Navigate to http://localhost:5166
```

### Build for Production

```bash
cd SocOps
dotnet build
```

Automatically deploys to GitHub Pages on push to `main`.

---

## 🌐 Open in GitHub Codespaces

No setup needed – code in the cloud:

1. Click **Use this template** on GitHub
2. Click **Code** → **Codespaces** → **Create codespace on main**
3. Wait for setup to complete
4. From the terminal: `cd SocOps && dotnet run`
5. Open the forwarded URL in your browser

---

## 📚 Learning Lab (5 Parts)

This repo is also a **hands-on workshop** for learning AI-assisted development with GitHub Copilot agents:

| Part | Title | Learn | Time |
|------|-------|-------|------|
| [**00**](workshop/00-overview.md) | Overview | Prerequisites & checklist | — |
| [**01**](workshop/01-setup.md) | Setup & Context | Workspace instructions, agent directives | 15 min |
| [**02**](workshop/02-design.md) | Design-First Frontend | UI redesign with Plan Mode, creative patterns | 15 min |
| [**03**](workshop/03-quiz-master.md) | Custom Quiz Master | Generative agents for custom themes | 10 min |
| [**04**](workshop/04-multi-agent.md) | Multi-Agent Development | TDD, code patterns, design reviews | 20 min |

[View full lab guide →](workshop/GUIDE.md)

---

## 💻 Development

### Key Commands

```bash
# Build
dotnet build SocOps/SocOps.csproj

# Run dev server (hot reload)
dotnet run --project SocOps

# Run tests
dotnet test

# Format code
dotnet format
```

### Pre-Commit Checklist

Before committing:
```
✅ dotnet build passes
✅ No unused variables or imports
✅ CSS utilities composed (no inline styles)
✅ Components use StateHasChanged() after state updates
```

### Architecture

```
SocOps/
├── Components/        # Reusable Blazor UI (GameScreen, BingoBoard, etc.)
├── Services/          # Business logic (BingoGameService, BingoLogicService)
├── Models/            # Data models (GameState, BingoSquareData, BingoLine)
├── Data/              # Static data (Questions.cs)
├── Pages/             # Routable pages (Home.razor)
├── Layout/            # Shared layout & navigation
└── wwwroot/           # Static assets & custom CSS utilities
```

[See Full Architecture](https://github.com/LimdaeIl/my-soc-ops-csharp/tree/main/SocOps)

---

## 🎨 Customize Your Game

### Add New Questions

Edit `SocOps/Data/Questions.cs`:

```csharp
public static List<string> QuestionsList = new()
{
    "Has worked in tech for 10+ years",
    "Speaks more than 2 languages",
    "Built a side project last year",
    // Add your questions here!
};
```

### Create a Custom Theme

Modify colors in `SocOps/wwwroot/css/app.css`:

```css
:root {
    --color-primary: #your-color;
    --color-accent: #your-accent;
}
```

See the [5-part lab](workshop/GUIDE.md) for advanced customization!

---

## 🤝 Contributing

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

**Note**: This project requires the Microsoft Contributor License Agreement (CLA). See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 📖 Resources

- **Workspace Instructions**: [.github/copilot-instructions.md](.github/copilot-instructions.md)
- **Design Guidelines**: [.github/instructions/blazor-component-design.instructions.md](.github/instructions/blazor-component-design.instructions.md)
- **CSS Reference**: [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md)
- **Blazor Docs**: [Microsoft Learn - Blazor](https://learn.microsoft.com/en-us/aspnet/core/blazor/)
- **Live Lab**: [dotnet-presentations.github.io](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/)

---

## 📄 License

This project is licensed under the **MIT License** – see [LICENSE](LICENSE) for details.

---

## 🎉 Ideas for Your Event

- **Tech Mixer**: Use the default tech-focused questions
- **Company Onboarding**: Create questions about the company and team members
- **Remote Team Build**: Host the game in a video call – participants share their screens
- **Classroom Activity**: Use for icebreakers and team connection (educational)
- **Conference Networking**: Generate questions relevant to the conference topic

---

## 🐛 Found a Bug?

Open an [issue](https://github.com/LimdaeIl/my-soc-ops-csharp/issues) and let us know! Include:

- Steps to reproduce
- Expected vs. actual behavior
- Browser/environment details

---

## 🚀 What's Next?

- [ ] Dark mode toggle
- [ ] Sound effects & animations
- [ ] Multiplayer leaderboard
- [ ] Community question database
- [ ] Mobile app (React Native)

Have an idea? [Start a discussion!](https://github.com/LimdaeIl/my-soc-ops-csharp/discussions)

---

**Built with ❤️ for team builders, made for AI-assisted development**
