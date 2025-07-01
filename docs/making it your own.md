## Making it your own

In the [HD (High Detail) Save](creating save files.md/#hd-high-detail-save) section in [Creating Save Files](creating save files.md), we discussed how ChatCon was initially designed to deal with continuity issues when developing software code. So the standard ChatCon source file comes "out of the box" containing only those instructions for contexts pertaining to the chat, subjects such as `current_focus`, `session_progression`, or `critical_insights`, for example. These are classified as contexts because they document the substance of the chat with the AI. With that in mind, the definition of "context" in ChatCon would be:

> **Context:** *1. The part of a text or statement that surrounds a particular word or passage and determines its meaning. 2. The circumstances in which an event occurs; a setting.*

So it makes sense that, for example, `session_progression` is considered a basic context that should be permanently carried as you move through AI chat sessions.

In ChatCon, there are three kinds of contexts:

- **Basic contexts:** We already discussed this one; `session_progression` is a basic context because it documents the progress of interactions between you and the AI.

- **Hard contexts:** These are project or technical in nature and can include information such as role definitions, project constraints, domain knowledge, methodology preferences, output formats, or quality standards, for example.

- **Soft contexts:** These are related to relationships, communication methods, or emotions, and they can include information on expertise level, communication style, language preferences, culture, accessibility needs, or emotional state awareness, for example.

### Managing contexts
Because people use AI assistants for just about anything you can think of, establishing and retaining—or *persisting*, which is how it's referred to in ChatCon—is just as crucial to establishing and persisting a basic context like `session_progression`.

In ChatCon you can manage contexts of all types using *context commands*. Below is a JSON example of the context commands you can invoke to permanently alter your ChatCon implementation:
```
"persistent_context_protocol": {
	"persist": "capture specified soft context and auto-include in future saves",
	"update": "refresh persistent soft context with current session analysis", 
	"drop": "remove persistence for specified context type",
	.
	.
	.
}
```

These command triggers, which also use the tilde symbol, are a bit like those used for the save outputs. At any time you can invoke these commands in your chat to have the AI create, modify, or delete a context of any type. The commands are:

- **~ persist:** This command permanently writes a context into the source block. So generating a save output with **~ SC** or **~ HD** will include your new context, which will remain until you remove it.

	> Remember that **~ EM**, the emergency save, doesn't generate and prepend a source output (.SRC) block, so a context change won't show up in a **~ EM** save because there's no source block to which to save the context. But generating a new source file with the command **~ SRC** will write out your new persisted context into that new source block.

- **~ update:** This command changes an existing context to that which you define in the command.

- **~ drop:** This command removes an existing context.

> Note: You can combine two commands together into a single line, like `~hd persist`. The AI isn't confused if you don't issue strict commands in a certain order or format.

### Context examples
This all can be a little confusing, so how about some examples? Let's start with some hard contexts:

#### Role definitions
	~ persist Roles: I'm the product manager, you're the technical consultant.
#### Project constraints
	~ update Project constraint: We now have a non-negotiable budget of $10,000.
#### Domain knowledge
	~ persist Terminology: JSON means JavaScript Object Notation.
#### Methodology preferences
	~ drop Methodology

And now for some soft context examples:
#### Expertise level
	~ persist Expertise: Assume expert knowledge
#### Communication style
	~ drop Tone
#### Language preferences
	~ update Language: Avoid jargon, use analogies, prefer bullet points vs prose.
#### Emotional state awareness
	~ persist Emotions: I'm a stressed, anxious student typing to understand.

And finally, some basic context examples.

> Caution: Most times when you interact with basic contexts, you'll want to use the **~ drop** command for various strategic reasons. Use caution when modifying these basic contexts. Replacing them is as easy as cutting and pasting text, but it might be troublesome to lose the contexts that track and preserve your session history.

#### session_progression
	~ drop session_progression
→ Perhaps because you have privacy concerns about preserving detailed history

#### key_technical_decisions
	~ drop key_technical_decisions
→ Perhaps because you're pivoting project direction entirely

#### deployment_readiness
	~ drop deployment_readiness
→ Perhaps because requirements changed significantly
		
#### current_status
	~ drop current_status
→ Perhaps because status is misleading after major changes

Of course, there may be times when a simple **~ update** will suffice rather than a **~ drop**. On the other hand, the **~ drop** functionality gives you surgical control over what context carries forward versus what gets intentionally forgotten.
	
### How to define a context
Actually, there's no real science to it. Except for using the command triggers, it's kind of up to you and the AI as to what and how to define a context, soft or hard.

A good example of this is the following context, which was created just to highlight the process for adding a context. The command entered was:
	`~ persist Tone: Make your responses chirpy, positive, encouraging, and supportive`, which resulted in the following JSON:
```
"persistent_contexts": {
   "tone": "chirpy, positive, encouraging, and supportive responses"
 }
```

Note that the structure of the command established "tone" as the first value in the `persistent_contexts` key.

Then the context was removed with the command `~ drop the tone context`, which resulted in the following JSON:
```
"persistent_contexts": {},
```

Then the context persistence was attempted with an ambiguous prompt: `Please make your responses to me in a chirpy, positive, encouraging, and supportive manner`, which resulted in the following JSON:
```
"persistent_contexts": {},
```

Woah! What happened?!? Where's the context? Simple—this is a *temporary* context; it's not persisted because the AI wasn't told to persist it. In fact, the AI responded with the following:

> This is actually a perfect test case for ChatCon - you've just given me a direct instruction about communication style, but it's NOT going into the persistent contexts because you used natural language instead of the persist command. So this tone guidance will stay active for our current conversation, but it won't automatically carry forward to future ChatCon sessions unless you explicitly persist it.

So let's try a properly formatted, yet still somewhat ambiguous prompt: `~ persist Please make your responses to me in a chirpy, positive, encouraging, and supportive manner`, and we're back to the following JSON:
```
"persistent_contexts": {
   "tone": "chirpy, positive, encouraging, and supportive responses"
 }
```

So the lesson here is that the AI will figure out what you want and define the appropriate JSON as long as you're using the proper context command trigger.
