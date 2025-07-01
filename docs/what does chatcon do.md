## What does ChatCon do?
It's simple, really: ChatCon gives the AI a framework for "remembering" the contents of the chat. The instructions in ChatCon tell the AI how to take notes for use in future chats. It's like a gaming "save file" you can trigger to use in the (inevitable) new chat. Here's how it works.

### The .SRC ("Source") block
The .SRC block (which I'll refer to as the *source block* from here on out) is a short set of instructions telling the AI how to take notes about the conversation. Here's the latest ChatCon source block:
```
{
"chatcon_type": "SRC",
"system": "ChatCon v0.5 - context preservation across AI chat sessions",
"version": "0.5",
"commands": {
"~em": "Emergency save (~40 tokens) - minimal context, NO SRC header - requires manual SRC prepending for restoration",
"~sc": "Save Checkpoint (~200 tokens) - moderate detail project state with embedded SRC", 
"~hd": "High Detail save (~500 tokens) - rich context with full progression tracking and embedded SRC",
"~src": "Output this bootstrap reference for fresh AI sessions"
},
"soft_context_commands": {
"persist": "~hd persist [type] - capture specified soft context and make persistent across sessions",
"update": "~hd update [type] - refresh persistent soft context with current session analysis",
"drop": "~hd drop [type] - remove persistence for specified context type",
"standard_types": ["style", "tone", "dynamics", "rapport"],
"examples": ["~hd persist style", "~sc update tone", "~hd drop dynamics"]
},
"usage_rules": [
"CRITICAL: SC and HD saves include embedded SRC and are self-contained",
"CRITICAL: EM saves are SRC-free for true emergency situations - manually prepend SRC for restoration",
"CRITICAL: AI must estimate tokens during generation and compress to 500 token hard limit",
"Commands are case-insensitive and space-tolerant: ~HD = ~hd = ~ hd = ~ HD etc",
"Commands work via implicit recognition - AI detects and responds automatically",
"SRC provides bootstrap knowledge so fresh AI understands the system",
"EM saves sacrifice self-containment for absolute minimal token usage",
"Soft context commands can be added to any save: ~hd persist style, ~sc update tone",
"Persistent contexts auto-carry forward in all subsequent saves until dropped"
],
"save_protocols": {
"em_protocol": "Minimal JSON without SRC - emergency use only when tokens critically low",
"sc_protocol": "Moderate detail with full embedded SRC - self-contained",
"hd_protocol": "Full detail with full embedded SRC - self-contained"
},
"persistent_context_protocol": {
"persist": "capture specified soft context and auto-include in future saves",
"update": "refresh persistent soft context with current session analysis", 
"drop": "remove persistence for specified context type",
"standard_types": "style (communication patterns), tone (emotional quality), dynamics (interaction patterns), rapport (relationship quality)",
"auto_carry": "persistent contexts automatically included in all subsequent saves until dropped",
"interpretation": "AI should interpret non-standard user requests and map to standard types or create appropriate custom categories",
"confirmation": "AI should confirm what persistent context was captured for user learning"
},
"compression_guidelines": {
"hd_target": "~500 tokens for optimal efficiency",
"compression_trigger": "when HD save exceeds ~800 tokens, compress automatically",
"compression_method": "preserve critical insights and current state, compress session_progression to key milestones only",
"maintain_context": "enough detail for seamless restoration without bloat",
"priority_order": "current_focus > key_decisions > critical_insights > compressed_progression > persistent_contexts"
},
"formats": {
"session_start": "Paste SRC alone to initialize ChatCon knowledge",
"project_continue_sc_hd": "Paste SC or HD save directly - they contain embedded SRC",
"project_continue_em": "Paste SRC + EM save together - EM saves are not self-contained",
"emergency_save": "~em produces minimal context without SRC overhead",
"checkpoint_save": "~sc produces moderate detail state with full embedded SRC",
"full_save": "~hd produces comprehensive context with full embedded SRC",
"soft_context_saves": "Add persist/update/drop commands to any save for soft context management"
},
"architecture": "SRC (system knowledge) + saves (project state) + persistent soft contexts = complete session independence. EM saves trade self-containment for emergency efficiency.",
"key_principle": "Context preservation > token efficiency, except in true emergency (EM) where minimal preservation > comprehensive context. Persistent soft contexts maintain relationship continuity across sessions."
}
```

For the uninitiated, this is JSON ([JavaScript Object Notation](https://en.wikipedia.org/wiki/JSON)), a method for exchanging information between computer systems. It's fairly readable, so at a glance you should be able to tell that the information here is presented in key/value pairs such that each key has a value. The key `chatcon_type`, for example (the first key in the block), contains the value "SRC." The "system" key contains the value "ChatCon v0.5 - context preservation across AI chat sessions," and so on. The AI uses these key/value combinations (which are called *objects*, hence the "O" in JSON) to understand how to take notes for use by its future self.

### How to use the SRC block
**When starting a new chat, just paste the source block into the AI.** You don't have to tell the AI what's going on or what the ChatCon system is; the AI can figure out ChatCon on its own. In fact, that's exactly how I tested it in my AI of choice, Claude: I simply pasted the source block into Claude and asked it, "What do you make of this?" It then told me exactly what the source block was for—it understood the system from reading the system itself. That's why ChatCon is called a "self-documenting" system: It carries its own meaning with it.

### Source block contents
Now, look in the source block for the key called "commands," which I'll re-create here:
```
  "commands": {
   "~em": "Emergency save (~40 tokens) - minimal context, NO SRC header - requires manual SRC prepending for restoration",
   "~sc": "Save Checkpoint (~200 tokens) - moderate detail project state with embedded SRC", 
   "~hd": "High Detail save (~500 tokens) - rich context with full progression tracking and embedded SRC",
   "~src": "Output this bootstrap reference for fresh AI sessions"  }
```

Notice there are four keys in this section:

- **~ em**
- **~ sc**
- **~ hd**
- **~ src**

They may be a little difficult to read, but each of these commands are preceded by a tilde symbol, which looks like this: **~** . Each command produces output of varying size. The one you should be familiar with by now is the **~ src** command which, you guessed it, produces the source block. If I entered the command **~ src**, the AI would output the entire source block you see in the section above: [The .SRC ("Source") block](what does chatcon do.md#the-src-source-block). Honestly, you would probably never need to output the source block like this, but the command is there if you need it.

> Note: Even though the commands are listed as [tilde] + [lowercase command], every command is case-insensitive and space-insensitive. If you prefer to use uppercase commands in ChatCon, that's fine. If you prefer to enter a space between the tilde symbol and the command, that's fine, too. You'll see commands in both uppercase and lowercase, and, although adding a space between the tilde and the command is optional, it's done here to make reading the command easier.

   The "save file" commands—EM, SC, and HD—are used to generate the save files. [Let's talk about them next.](creating save files.md)

   > **But first, this:** I won't go over the other keys in the source block in detail, but they're still pretty important. The `soft_context_commands`, `usage_rules`, `save_protocols`, as well as all the others, are instructions to the AI about how ChatCon should work. I'll refer to these keys later, but for now you should be able to understand what they do by reading the values associated with each key.
