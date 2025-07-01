# How to use the ChatCon system
Let's cut to the chase with some easy-to-follow steps for using ChatCon:

1. **Install the system:** For every brand new chat where you don't have any continuity, paste the `.SRC`/[source block](https://github.com/JohnChatConner/ChatCon/blob/main/chatcon-src-v1.0.json) into the chat window and send it to the AI. That's it. That's the "install" process. 

	For example, if you wanted to start a conversation about, say, dinosaurs, you'd start a new chat in your AI of choice, paste the source block into the AI, and begin interacting with it.

2. **Periodically generate a save output:** Ask a question, get a response, create a save file to capture the interaction. For example, you can:

	- Periodically run **~ GC** after every interaction pair to closely track the conversation. The benefit of the periodic **~ GC** save is that you'll create a running set of save outputs that will document every interaction, without spending a lot of tokens to do so. Each subsequent GC will document all the previous interactions prior to the save command, so you'll always have an up-to-date save file, and you won't be surprised if you suddenly run out of tokens. Generating this many saves may use more tokens than necessary, but the only context you might ever lose is that last interaction before token depletion.
	
	- Instead of multiple **~ GC** save outputs, run a single **~ HD** command to generate a large save output at the end of the conversation. This will capture all the interactions in the chat (just like a running set of GC commands), but if you know you're at a good stopping point, the HD will give you a really comprehensive output.
	
3. **Restore context and continuity:** When it's time to start a new chat, copy the latest save output from the old chat, paste it into the new chat window, and start interacting with the AI. It will remember what you were discussing by reading and referring to its own notes from the ChatCon output you pasted.

> **Note:** Except for the EM output, you won't need to paste the source block into the AI every time you continue a chat. Use the `.SRC`/source block only when you want to start collecting context for a new conversation.