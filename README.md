# ChatCon
ChatCon ("Chat Continuity") is a meta-prompt designed to maintain continuity between sessions; it carries context from one AI chat session to another.

## Context preservation across AI chat sessions
Most AI assistants forget everything the moment you start a new chat. This gets old fast when you're working on anything substantial, like coding projects, research, or even just having ongoing conversations that matter to you.
ChatCon is a meta-prompt system that gives your AI a framework for taking notes about your conversations. Think of it as a save file system for chat sessions.

## The Problem
AI chat sessions have token limits. When you hit that limit, you start over from scratch. If you're coding something complex, debugging an issue, or having a meaningful conversation, losing that context is frustrating and wasteful.
Sure, you could manually summarize what happened, but that's error-prone and eats into your token budget. Plus, you'll inevitably forget important details.

## How ChatCon Works
ChatCon is self-documenting; the AI figures out how to use it just by reading the system prompt. You paste a JSON block into a new chat, and the AI understands it should start taking notes.
When you're ready to wrap up a session, you trigger a save command:
- `~em` - Emergency save (around 40 tokens) when you're almost out
- `~sc` - Save checkpoint (around 200 tokens) for moderate detail
- `~hd` - High detail save (around 500 tokens) for comprehensive context
Copy that save output, paste it into your next chat, and the AI picks up exactly where you left off.

## Quick Start
1. **Start a new chat:** Paste the ChatCon source block (see `ChatCon/chatcon-src-v1.0.json`
2. **Work normally:**Ask questions, write code, whatever you're doing
3. **Save before you run out of tokens:** Use `~sc` or `~hd` to generate a save
4. **Continue in a new chat:** Paste the entire save output and keep going
The AI doesn't need special instructions because it reads it's own JSON notes and knows what to do.

## Save File Types
**Emergency (`~em`):** Bare minimum context when you're about to hit token limits. Doesn't include the system prompt, so you'll need to prepend it manually if restoring from an emergency save.
**Save Checkpoint (`~sc`):** Good middle ground. Captures key context without being verbose. Includes embedded system prompt, so it's self-contained.
High Detail (`~hd`): Comprehensive save with full progression tracking. Can get large but includes automatic compression when it exceeds ~800 tokens.

## Context Management
ChatCon lets you persist specific types of context across sessions:
```
~ persist tone: Keep responses concise and technical
~ persist role: You're a senior developer, I'm learning
~ update constraints: Budget is now $5000, not $10000  
~ drop methodology: No longer using agile approach
```

These contexts stick around until you explicitly remove them, which is useful for maintaining consistent AI behavior across long projects.

## Real-World Usage
**Coding projects:** Maintain context about architecture decisions, current bugs, feature requirements, and code structure across multiple debugging sessions.
**Research:** Keep track of findings, sources, hypotheses, and conclusions as you work through complex topics over time.
**Creative work:** Preserve character details, plot points, style guidelines, and feedback loops for writing projects.
**Learning:** Maintain your current knowledge level, learning style preferences, and progress through complex subjects.

## Advanced Features
**Soft context persistence:** Maintain communication style, expertise assumptions, and relationship dynamics across sessions.
**Automatic compression:** HD saves are intelligently compressed when they get too large, preserving critical information and staying under token limits.
**Cross-platform compatibility:** Works with Claude, ChatGPT, and other major AI assistants (JSON parsing is pretty universal).

## Examples
See the `examples/` directory for real ChatCon saves from actual projects. These show how the system captures context for different types of work.

## Making It Your Own
The source block is just JSON—modify it to suit your needs. Add custom context types, change compression rules, or adjust save detail levels. The system is designed to be hackable.

## Limitations
ChatCon doesn't capture everything. Tone of voice and emotional nuance don't always come through perfectly. It's optimized for preserving factual context and project state, not for replicating the full conversational feel.
Emergency saves are genuinely minimal. If you're relying on them regularly, you're probably cutting things too close.

## FAQ
**Q: Does this work with [my AI assistant]?**
If it can parse JSON and follow instructions, probably. Tested extensively with Claude and ChatGPT.

**Q: How much overhead does this add?**
The source block takes up around 300 tokens. Save checkpoints are around 200 tokens. It's overhead, but it's usually worth it for non-trivial conversations.

**Q: Can I automate this?**
For now, the system is designed for manual triggers. Automating save generation would be possible but isn't built in.

**Q: What if I forget to save?**
You lose context, same as always. ChatCon doesn't solve the fundamental problem of remembering to save, it just makes saving and restoring much more effective when you do it.

---

ChatCon is a tool, not magic. It won't make AIs remember everything perfectly, but it will give you much better continuity than starting from scratch every time you hit a token limit.
