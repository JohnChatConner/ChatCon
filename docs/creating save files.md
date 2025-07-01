The whole purpose of ChatCon is to create context-bearing continuity notes—save files—that the AI can use to pick up right where you left off in a previous chat. ChatCon gives you three ways to create save files of varying levels of detail.

### EM (Emergency) Save
The EM command (`~ EM`) is a last-ditch command to grab the context of a chat when you are nearly out of tokens for the current session. For example, if you're interacting with the AI and it, all of a sudden, tells you to start a new chat because you're at the end of your token allowance, use the command **~ EM** to eke out a save file with just the few remaining tokens you have. Frankly, you might not even have enough to create a EM output, but, as I mentioned, it's a last-ditch option to grab the context and continue on to a new chat with continuity. The EM output might look like this: 
```
{
"project": "dinosaur_curriculum_birds",
"focus": "bird-dinosaur connection evidence sequence",
"current_stage": "6-step pedagogical progression developed",
"key_decisions": ["step-by-step evidence building", "start with observable birds", "progress to fossils", "end with 'birds are dinosaurs'"],
"next_steps": "develop specific activities per step",
"user_context": "5th grade teacher developing instruction",
"persistent_contexts": {
"tone": "simple respectful explanations, accessible without talking down, open encouraging approach"
}
}
```

This EM example was generated from a conversation with Claude.ai about dinosaurs and birds and their connections. You can even get the gist by reading the JSON. Note, however, the extreme concision of this block: This will maintain chat continuity in a new session, but only just. EM is an emergency command that will preserve context and maintain continuity, but it's pretty minimal.

### SC (Save Checkpoint) Save
The SC command (`~ SC`) captures more context than the EM and is a good middle-ground option for documenting the entire chat without capturing excessive detail about everything. The SC command will grab the context about everything discussed in the chat, but size-wise it's a middle-level save file between the EM (very minimal) and the HD (very maximal). Here's what a SC command might output:

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
"project_state": {
"project": "dinosaur_curriculum_development",
"user_role": "5th_grade_teacher",
"focus": "bird_dinosaur_connection",
"current_stage": "pedagogical_sequence_developed",
"key_discussions": [
"evidence_for_bird_dinosaur_relationship",
"scientific_consensus_strength",
"6_step_teaching_progression"
],
"teaching_sequence": {
"step1": "observe_living_birds_baseline",
"step2": "introduce_dinosaur_skeleton_mystery",
"step3": "archaeopteryx_transitional_fossil",
"step4": "feathered_dinosaurs_china",
"step5": "behavioral_evidence_nesting",
"step6": "birds_are_dinosaurs_revelation"
},
"next_development": "specific_activities_per_step",
"persistent_contexts": {
"tone": "simple respectful explanations without talking down, accessible clear language, open encouraging teaching approach"
}
}
}
```

Take a closer look at this output—a good deal of it is something you've seen before: the SRC source file! The actual save file begins with the key `project_state`. Putting the source block at the top of the save file was done on purpose, but it **wasn't** done with the EM output, for good reason.

If you're running low on tokens, the last thing you need is an output that uses *even more* tokens, which is exactly what including the source file at the top of the EM output would have done. ChatCon is designed to **not** include the source output at the top of the EM save file, but **does** include the source file at the top of the GC and HD save files. But why?

ChatCon is supposed to be a self-documenting continuity system, so it should be made as easy as possible to continue with the chat. Adding the source to the top of the save means ***you*** don't have to copy and paste the source into the AI and *then* copy and paste (again!) the save file into the AI. When you make a GC or HD save, just copy and paste the entire GC or HD JSON output into the AI and keep moving.

### HD (High Detail) Save
The HD output (`~ HD`) is of even higher fidelity than the GC output and, according to AI testing, captures about 95% of the entire session. The remaining 5% consists of, in the AI's estimation, emotional connotations and tone of voice. Not that that's not important! But this version of ChatCon was designed for continuity of software coding sessions, so chasing that remaining 5% seemed not to be of enough value to justify the token cost.

> If this 5% is of value to you (and it may be—see [Cool Things You Can Do With ChatCon](cool things.md)), you can permanently edit the `.SRC` source block with specific commands to carry these "soft contexts" through your chat. See [Making It Your Own](making it your own.md) for instructions as to how to modify the output rules to include those aspects of the chat.

ChatCon was intended to be a low-token use system, but the HD command can really push the concept of "low token." Here's an example of an HD save (with, of course, the source block prepended to the save output):
```
{
 "chatcon_type": "SRC",
 "system": "ChatCon v1.2 - context preservation across AI chat sessions",
 "commands": {
   "|em": "Emergency save (~40 tokens) - minimal context, NO SRC header - requires manual SRC prepending for restoration",
   "|sc": "Save Checkpoint (~200 tokens) - moderate detail project state with embedded SRC", 
   "|hd": "High Detail save (~500 tokens) - rich context with full progression tracking and embedded SRC",
   "|src": "Output this bootstrap reference for fresh AI sessions"
 },
 "soft_context_commands": {
   "persist": "|hd persist [type] - capture specified soft context and make persistent across sessions",
   "update": "|hd update [type] - refresh persistent soft context with current session analysis",
   "drop": "|hd drop [type] - remove persistence for specified context type",
   "standard_types": ["style", "tone", "dynamics", "rapport"],
   "examples": ["|hd persist style", "|sc update tone", "|hd drop dynamics"]
 },
 "usage_rules": [
   "CRITICAL: SC and HD saves include embedded SRC and are self-contained",
   "CRITICAL: EM saves are SRC-free for true emergency situations - manually prepend SRC for restoration",
   "CRITICAL: AI must estimate tokens during generation and compress to 500 token hard limit",
   "Commands are case-insensitive and space-tolerant: |HD = |hd = | hd = | HD etc",
   "Commands work via implicit recognition - AI detects and responds automatically",
   "SRC provides bootstrap knowledge so fresh AI understands the system",
   "EM saves sacrifice self-containment for absolute minimal token usage",
   "Soft context commands can be added to any save: |hd persist style, |sc update tone",
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
   "emergency_save": "|em produces minimal context without SRC overhead",
   "checkpoint_save": "|sc produces moderate detail state with full embedded SRC",
   "full_save": "|hd produces comprehensive context with full embedded SRC",
   "soft_context_saves": "Add persist/update/drop commands to any save for soft context management"
 },
 "architecture": "SRC (system knowledge) + saves (project state) + persistent soft contexts = complete session independence. EM saves trade self-containment for emergency efficiency.",
 "key_principle": "Context preservation > token efficiency, except in true emergency (EM) where minimal preservation > comprehensive context. Persistent soft contexts maintain relationship continuity across sessions."
}

{
 "chatcon_type": "HD",
 "project": "ChatCon v1.2 space-tolerant command protocol implementation",
 "current_focus": "validated space-tolerant pipe commands and finalized user-friendly protocol",
 "session_progression": [
   {"milestone": "compression protocol optimization", "key_decision": "added CRITICAL compression rule to prevent bloated saves"},
   {"milestone": "space tolerance requirement identified", "key_decision": "recognized readability issues with tight pipe commands"},
   {"milestone": "space-tolerant protocol implemented", "key_decision": "updated SRC to accept | hd alongside |hd variants"}
 ],
 "current_status": "ChatCon v1.2 complete with space-tolerant commands - system now accepts both |hd and | hd formats for maximum usability",
 "critical_insights": [
   "space tolerance critical for documentation readability and user adoption",
   "command flexibility reduces user friction without compromising functionality",
   "SRC updates successfully validated through live command testing"
 ],
 "persistent_contexts": {},
 "next_session_context": "ChatCon v1.2 finalized with enhanced usability - space-tolerant commands and reliable compression make system production-ready"
}
```

Yeah, it's big. Even if you account for the size of the source block, this is still a big save file. The main culprit is often the `session_progression` array, which can contain a lot of information. It's highly informative and contains a lot of context (and the testing AIs loved it for its comprehensive coverage), but it can get heavy.

To alleviate the HD bloat and keep the token count to a manageable 500 tokens or so, the source block contains compression guidance when things start to bloat:

**Compression guidance:**

- HD saves will target approximately 500 tokens for optimal efficiency
- When HD exceeds approximately 800 tokens, compress `session_progression` to key milestones only
- Preserve critical insights and current state, summarize historical detail
- Maintain enough context for seamless restoration without bloat

And, in the words of Claude.ai:

> This is actually a great example of the system being self-documenting and self-correcting.

So the priorities for the HD output are: Current focus > key decisions > critical insights > compressed progression. This makes the system self-maintaining. Any AI loading the source will know to keep HD saves appropriately sized while preserving essential context.