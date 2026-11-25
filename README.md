# Aember for Claude Code

[Aember](https://aember.app) is a native Mac code editor that records every change to your project, saved or not, and who made it: you, Claude Code, or another agent. When Claude gets one change wrong, you take out just that change, in every file it touched, and keep everything after it.

This plugin connects Claude Code to Aember:

- **Opens the project in Aember.** When a session starts in a git repository or an Aember project, the plugin opens it in Aember, launching Aember in the background if it isn't running. Aember stays behind your terminal.
- **Has Claude work through Aember.** Claude is told, at the start of each session, to read, search and edit the project's files with Aember's tools, which see your unsaved changes and record every change in History. No instructions in CLAUDE.md are needed.
- **Records Claude's own edits.** When Claude edits with its own Edit and Write tools, Aember records the change as Claude Code's, so you can undo it like any other.
- **Optionally, routes file tools to Aember.** With **Route file tools through Aember** on, Claude Code's own Read, Edit, Write and Grep are refused for the project's files, and Claude uses Aember's tools instead. Read still opens images and PDFs.

## You need

- A Mac with macOS 15 or later, on Apple silicon.
- [Aember](https://aember.app/download). It's free to use as an editor. Its MCP server, which Claude talks to, needs a license ($15, once) or the free two-week trial.

## Install

```bash
claude plugin install aember --marketplace bitarts-ltd/aember-claude-plugin
```

Claude Code asks for the plugin's options when you enable it. The defaults work for most people.

| Option | Default | What it does |
|---|---|---|
| Open projects in Aember | on | Opens a session's git repository or Aember project in Aember. Off: only projects already open in Aember are used. |
| Route file tools through Aember | off | Refuses Claude's own Read, Edit, Write and Grep on the project's files, so every change goes through Aember. |
| Aember MCP server | `http://127.0.0.1:56891/mcp` | Aember's server address, from the Endpoint row of Aember's Settings > MCP. |
| Aember app | empty | The Aember.app to launch. Empty uses /Applications/Aember.app. |

If you connected Claude Code to Aember by hand before (`claude mcp add … aember`), remove that server with `claude mcp remove aember`, so Claude doesn't see Aember's tools twice. Aember's per-project Claude Code hooks (Settings > MCP > Install Hooks) aren't needed with the plugin either.

## When Aember isn't running

If Aember isn't running when a session starts, the plugin launches it, and Claude Code may have tried to connect before Aember was ready. Claude is told to ask you to run `/mcp` and reconnect `aember` if its tools are missing. Route file tools through Aember never refuses Claude's own tools until Claude Code has connected to Aember in that session.

## Privacy

The plugin talks only to Aember, on your Mac (127.0.0.1). It sends nothing anywhere else. See Aember's [privacy policy](https://aember.app/privacy/).

## License

MIT. See [LICENSE](LICENSE).
