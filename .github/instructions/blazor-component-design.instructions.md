---
name: blazor-component-design
description: "Use when: designing or refactoring Blazor components (*.razor files), creating themed game screens, building interactive UI elements, or implementing animations in SocOps. Combines Blazor patterns with creative, distinctive aesthetics for the social bingo game context."
applyTo: "**/Components/**/*.razor"
---

# Blazor Component Design for Soc Ops

Design interactive, visually distinctive Blazor components that elevate the social bingo game experience. This instruction combines creative UI principles with Blazor-specific technical patterns.

---

## Core Principles

### 1. **Aesthetic Over Generic**

Avoid placeholder aesthetics. Commit fully to a distinctive visual direction that matches the component's context:

- **Game Screen**: Bold, energetic, celebratory (high-contrast, sharp typography, micro-interactions)
- **Start Screen**: Welcoming, clear, inviting (generous spacing, readable hierarchy, smooth entries)
- **Modals**: Focused, modular, purposeful (layered depth, clear call-to-action, context-aware styling)
- **Squares**: Tactile, responsive, playful (state clarity, animated feedback, personality)

### 2. **Match Implementation to Vision**

- **Maximalist design** (Cyberpunk, Retro): Elaborate animations, multi-layer backgrounds, complex effects
- **Minimalist design** (Zen, Brutalist): Precision typography, whitespace mastery, subtle micro-interactions
- **Animated entry** (Page load): Staggered component reveals with `animation-delay` for orchestrated impact

### 3. **Context-Specific Creativity**

This is a **social team-building game**. Design should reflect:
- **Fun & Energy**: Celebrations matter—winning should *feel* epic
- **Clarity & Responsiveness**: Players need instant feedback on square clicks
- **Inclusivity**: Account for color-blind users (avoid red/green only distinctions)
- **Mobile-First**: Support small screens without sacrificing flair

---

## Blazor Component Patterns

### Responsive Layout Structure

```razor
<div class="flex flex-col items-center justify-center min-h-full">
    <!-- Header -->
    <header class="w-full px-4 py-6 text-center">
        <h1 class="text-5xl font-bold">Title</h1>
    </header>

    <!-- Main Content -->
    <main class="flex-1 flex items-center justify-center w-full px-4">
        <!-- Game board or content -->
    </main>

    <!-- Footer (optional) -->
    <footer class="w-full px-4 py-4 text-center text-gray-600">
        <!-- Info or buttons -->
    </footer>
</div>
```

### Component Lifecycle & State Management

```csharp
@code {
    [Parameter]
    public EventCallback<GameState> OnStateChanged { get; set; }

    private GameState CurrentState = new();

    protected override async Task OnInitializedAsync()
    {
        // Initialize component state
        StateHasChanged();
    }

    private async Task HandleInteraction()
    {
        // Update state
        CurrentState.UpdateProperty();
        
        // Notify parent & trigger StateHasChanged()
        await OnStateChanged.InvokeAsync(CurrentState);
        StateHasChanged();
    }
}
```

### Mobile-Responsive Grid (Bingo Board)

```razor
<div class="grid gap-1" style="grid-template-columns: repeat(auto-fit, minmax(60px, 1fr));">
    @for (int i = 0; i < Squares.Count; i++)
    {
        <div class="aspect-square">
            <BingoSquare 
                Square="Squares[i]"
                OnClick="() => SelectSquare(i)" />
        </div>
    }
</div>
```

---

## CSS Animation Patterns

### High-Impact Page Load

Add to `wwwroot/css/app.css`:

```css
/* Staggered entry animation */
@keyframes slideInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animate-slide-in {
    animation: slideInUp 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.animate-slide-in-delay-1 { animation-delay: 0.1s; }
.animate-slide-in-delay-2 { animation-delay: 0.2s; }
.animate-slide-in-delay-3 { animation-delay: 0.3s; }
```

Apply in Razor:

```razor
<header class="animate-slide-in animate-slide-in-delay-1">
    <h1>Title</h1>
</header>
<main class="animate-slide-in animate-slide-in-delay-2">
    <!-- Content -->
</main>
```

### Square Selection Feedback

```css
@keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.08); }
}

@keyframes checkmark {
    0% { transform: scale(0) rotate(-45deg); }
    50% { transform: scale(1.2); }
    100% { transform: scale(1); }
}

.square-selected {
    animation: pulse 0.4s ease-out;
}

.checkmark-enter {
    animation: checkmark 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

### Win State Celebration

```css
@keyframes confetti-fall {
    0% {
        opacity: 1;
        transform: translateY(-20px) rotate(0deg);
    }
    100% {
        opacity: 0;
        transform: translateY(200px) rotate(720deg);
    }
}

.winner-animation {
    animation: confetti-fall 1s ease-out forwards;
}
```

---

## Theme Palette Examples

Choose **one** dominant aesthetic per component/game mode:

### 🎮 Cyberpunk Neon
- **Primary**: `#00ff00` (neon green)
- **Secondary**: `#ff00ff` (hot magenta)
- **Accent**: `#00ffff` (cyan)
- **Background**: `#0a0e27` (dark navy)
- **Font**: Courier New, monospace (tech aesthetic)
- **Effects**: Glow layers, scanlines, distortion

### 🕹️ Retro Arcade
- **Primary**: `#ffcc00` (golden yellow)
- **Secondary**: `#ff0099` (arcade pink)
- **Accent**: `#00ccff` (arcade blue)
- **Background**: `#1a1a2e` (dark with purple tint)
- **Font**: Pixel fonts or bold sans-serif
- **Effects**: Pixelated borders, blinking text, 8-bit sounds (CSS animations only)

### 🌙 Minimalist Zen
- **Primary**: `#2563eb` (soft blue)
- **Secondary**: `#f3f4f6` (light gray)
- **Accent**: `#10b981` (gentle green)
- **Background**: `#ffffff` (pure white) or `#f9fafb` (off-white)
- **Font**: Modern sans-serif (Trebuchet, system fonts)
- **Effects**: Smooth transitions, generous whitespace, no hard edges

### 🌺 Soft Pastel
- **Primary**: `#ec4899` (rose)
- **Secondary**: `#a78bfa` (lavender)
- **Accent**: `#34d399` (mint)
- **Background**: `#faf5ff` (pale lavender)
- **Font**: Rounded sans-serif
- **Effects**: Gradient overlays, soft shadows, subtle animations

---

## Implementation Checklist

When creating or redesigning a component:

- [ ] **Define aesthetic direction** explicitly (not generic)
- [ ] **Choose a dominant color palette** with primary, secondary, accent
- [ ] **Select distinctive typography** (not system-ui unless intentional minimalism)
- [ ] **Plan one high-impact animation** (page load, win state, interaction feedback)
- [ ] **Mobile-first responsive design** (test at 320px, 768px, 1200px)
- [ ] **Use CSS utilities from `app.css`** consistently (no inline styles)
- [ ] **Add new utilities to `app.css`** as needed, following existing patterns
- [ ] **Test state management** (component updates trigger StateHasChanged())
- [ ] **Keyboard accessible** (buttons via `onclick`, form controls, focus states)
- [ ] **Include dark mode considerations** (CSS variables for theme switching)

---

## File Organization

```
Components/
├── BingoBoard.razor           # Grid + win detection logic
├── BingoSquare.razor          # Individual square (state, feedback)
├── BingoModal.razor           # Modal wrapper & animations
├── GameScreen.razor           # Main game UI orchestration
├── StartScreen.razor          # Welcome & theme selection
└── Shared/
    └── [theme-specific].razor # Theme variants (e.g., CyberpunkBoard.razor)
```

Store theme-specific CSS in section tags within components or add to `app.css` with prefixes:

```css
/* Cyberpunk theme */
.board-cyberpunk { /* ... */ }
.square-cyberpunk { /* ... */ }
.board-cyberpunk .square-selected { /* ... */ }
```

---

## Do's ✅

- **Do** use CSS variables for theme colors (`:root { --primary: #...}`)
- **Do** layer animations (background + text + border reveal separately)
- **Do** test on mobile devices or browser DevTools responsive mode
- **Do** reference the broader social bingo context (team building, fun, celebration)
- **Do** use `BingoGameService` events to coordinate multi-component updates
- **Do** provide clear visual feedback for all interactive elements
- **Do** document complex animation logic with comments

## Don'ts ❌

- Don't use generic fonts (Arial, Helvetica, Inter without context)
- **Don't** default to purple gradients or clichéd color combinations
- **Don't** add animations that distract from game interaction
- **Don't** forget mobile device users (no fixed layouts)
- **Don't** mix multiple competing aesthetic directions in one component
- **Don't** use inline styles—compose CSS utilities instead
- **Don't** assume all users see color the same way (test color contrast)

---

## Example: Redesigned Start Screen

**Vision**: Energetic, welcoming, modern

```razor
@* StartScreen.razor *@
<div class="flex flex-col items-center justify-center min-h-full bg-gradient-to-br from-blue-50 to-indigo-100">
    
    <header class="animate-slide-in animate-slide-in-delay-1 text-center mb-8">
        <h1 class="text-5xl font-bold text-gray-900 mb-2">Soc Ops</h1>
        <p class="text-lg text-gray-600">Social Bingo for Team Building</p>
    </header>

    <main class="animate-slide-in animate-slide-in-delay-2 text-center space-y-4">
        <div class="bg-white p-6 rounded-xl shadow-xl max-w-md">
            <h2 class="text-2xl font-bold text-gray-900 mb-4">How to Play</h2>
            <ul class="text-left space-y-2 text-gray-700">
                <li>🔍 Find people who match the questions</li>
                <li>✅ Tap a square when you find a match</li>
                <li>🏆 Get 5 in a row to win!</li>
            </ul>
        </div>

        <button class="animate-slide-in animate-slide-in-delay-3 px-8 py-4 bg-blue-600 text-white text-lg font-bold rounded-lg shadow-lg hover:bg-blue-700 transition-colors duration-150">
            Start Game
        </button>
    </main>
</div>

@code {
    private async Task StartGameHandler()
    {
        await OnGameStart.InvokeAsync();
    }
}
```

---

## Resources

- **CSS Utilities Reference**: [css-utilities.instructions.md](./css-utilities.instructions.md)
- **Blazor Docs**: https://learn.microsoft.com/aspnet/core/blazor/
- **Responsive Design**: Test with browser DevTools (F12 → Toggle device toolbar)
- **Color Tools**: https://coolors.co (palette generation)
- **Animation Reference**: https://animista.net (CSS animation inspiration)

**Remember:** Extraordinary design comes from committing fully to a distinctive vision and executing it with precision.
