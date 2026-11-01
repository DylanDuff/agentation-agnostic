<picture>
  <source media="(prefers-color-scheme: dark)" srcset="package/logo-dark.svg">
  <img src="package/logo.svg" alt="Agentation" width="180">
</picture>

<br>

[![npm version](https://img.shields.io/npm/v/agentation)](https://www.npmjs.com/package/agentation)
[![downloads](https://img.shields.io/npm/dm/agentation)](https://www.npmjs.com/package/agentation)

**[Agentation](https://agentation.com)** is an agent-agnostic and framework-agnostic visual feedback tool. Click elements on your page, add notes, and copy structured output that helps AI coding agents find the exact code you're referring to.

## Packages

Every package renders the same shared toolbar from [`@agentation/core`](package-core/README.md), so features and fixes land in all of them at once.

| Framework | Package | Docs |
| --- | --- | --- |
| React 18+ | `agentation` | [package README](package/README.md) |
| Vue 3.5+ | `agentation-vue` | [package README](package-vue/README.md) |
| Svelte 4 and 5 (incl. SvelteKit) | `agentation-svelte` | [package README](package-svelte/README.md) |
| Angular, plain HTML, or any other framework | `agentation-element` (`<agentation-feedback>` custom element) | [package README](package-element/README.md) |

In development builds the toolbar names the React, Vue, Svelte, or Angular components around each annotated element.

## Install

```bash
npm install agentation -D   # or agentation-vue, agentation-svelte, agentation-element
```

## Usage

The React example is below. See each package README for its framework's usage.

```tsx
import { Agentation } from 'agentation';

function App() {
  return (
    <>
      <YourApp />
      <Agentation />
    </>
  );
}
```

The toolbar appears in the bottom-right corner. Click to activate, then click any element to annotate it.

## Connect to your agent

Copied feedback works with Claude Code, Codex, Gemini, Grok, or any AI tool.
For direct sync, register `npx -y agentation-mcp server` with your MCP client and
connect the toolbar to its HTTP endpoint:

```tsx
<Agentation endpoint="http://localhost:4747" />
```

Keep the agent running, add a test annotation, and ask it to read the feedback.
See the [setup guide](https://agentation.com/install#agent-integration).

## Features

- **Click to annotate** – Click any element with automatic selector identification
- **Text selection** – Select text to annotate specific content
- **Multi-select** – Hold Cmd/Ctrl to select elements individually, or drag to select multiple at once
- **Area selection** – Drag to annotate any region, even empty space
- **Animation pause** – Pause supported CSS animations, Web Animations, and videos to capture specific states
- **Structured output** – Copy markdown with selectors, positions, and context
- **Embedded pages** – Select elements in open shadow roots and same-origin iframes
- **Integration options** – Capture identifying attributes, choose metadata-only Copy formats, and open detected source locations through your editor integration
- **Hash routes** – Opt in to separate annotations and sessions for each hash route
- **Dark/light mode** – Toggle in settings, persists to localStorage
- **Zero dependencies** – No runtime libraries beyond your framework's peer dependencies (the non-React packages bundle Preact internally)

See the [React package README](package/README.md) for props and integration examples. The other packages take the same options.

## How it works

Agentation captures class names, selectors, and element positions so AI agents can `grep` for the exact code you're referring to. Instead of describing "the blue button in the sidebar," you give the agent `.sidebar > button.primary` and your feedback.

## Requirements

- One of the frameworks listed under [Packages](#packages), or none with `agentation-element`
- Desktop browser (mobile not supported)

## Docs

Full documentation at [agentation.com](https://agentation.com)

Developer reference:

- [Toolbar to server sync](docs/server-sync.md): how stored annotations map to server IDs, what gets uploaded, and how agent resolutions reach the page

## License

© 2026 Benji Taylor

Licensed under PolyForm Shield 1.0.0
