# Contributing to ChatCon
Welcome to ChatCon, a system for preserving context across AI chat sessions! We’re thrilled you’re here to help shape its future. Whether you’re reporting bugs, suggesting features, or submitting code, your contributions make ChatCon better for everyone. This guide explains how to contribute via GitHub Issues, Discussions, or pull requests (PRs).

## Getting Started

- **Explore the Project:** Check out the [README](https://github.com/JohnChatConner/ChatCon#) to understand ChatCon’s purpose, commands (like  `~hd`,  `~sc`,  `~em`,  `~persist`,  `~update`, and `~drop`), and soft context protocols.

- **Join the Community:** Visit our [GitHub Discussions](https://github.com/JohnChatConner/ChatCon/discussions) to share ideas or ask questions.

- **Follow the Code of Conduct:** Be respectful and inclusive in all interactions.

## Submitting Feedback
Have a bug to report or a feature idea? Here’s how to share your thoughts:

1. **Check for Existing Issues:** Search the [Issues](https://github.com/JohnChatConner/ChatCon/issues) tab to avoid duplicates.
2. **Open an Issue:**
  	- Go to the “Issues” tab and click “New issue.”
	- Choose a template (e.g., Bug Report, Feature Request) and fill in details like steps to reproduce or use cases.
	- Example: Suggest a new archive command to store old saves, describing its purpose and benefits.
3. **Join Discussions:** For general ideas or brainstorming (e.g., new soft context types), post in [Discussions](https://github.com/JohnChatConner/ChatCon/discussions).
4. **Be Clear:** Include relevant details, like ChatCon version (0.5) or example scenarios.

We’ll respond to issues and discussions promptly to keep the conversation flowing!

## Contributing Code or Documentation

Do you want to add a feature, fix a bug, or improve documentation? Follow these steps to submit a pull request (PR):

1. **Fork the Repository:**
	- Click “Fork” on [https://github.com/JohnChatConner/ChatCon](https://github.com/JohnChatConner/ChatCon).
	- Clone your fork to your local machine: `git clone https://github.com/YOUR_USERNAME/ChatCon.git`.
2. **Create a Feature Branch:**
	- Create a new branch for your work: `git checkout -b feature/your-feature-name` (e.g., `feature/archive-command`).
	- Keep changes focused (e.g., one new command or doc update per branch).
3. **Make Changes:**
	- Code contributions should align with ChatCon’s JSON-based save format and token limits (500 for `hd`, ~200 for `~sc`).
	- Documentation updates should use clear markdown and match ChatCon’s style.
	- Test your changes locally to ensure they work.
4. **Commit and Push:**
	- Commit changes with a clear message: `git commit -m "Add ~archive command for storing old saves"`.
	- Push to your fork: `git push origin feature/your-feature-name`.
5. **Open a Pull Request:**
	- Go to your fork on GitHub and click “Compare & pull request.”
	- Use the PR template to describe your changes, linking to related issues.
	- Submit the PR and wait for review.
6. **Address Feedback:**
	- Respond to review comments and push updates to the same branch if changes are requested.
	- We’ll review for code quality, alignment with ChatCon’s architecture, and token efficiency.
7. **Merge and Celebrate:**
	- Once approved, we’ll merge your PR into the `main` branch.
	- You’ll be credited here for your contributions!

## Contribution Ideas
Here are some areas where you can contribute:

- **New Commands:** Propose commands like `~archive` or `~compare` for save management.
- **Soft Context Enhancements:** Add new types (e.g., `priority` for task focus) or improve persistence logic.
- **Documentation:** Clarify usage of `~hd`, `~sc`, or `~em` saves or add examples.
- **Testing:** Add tests for JSON save compression or command parsing.
- **Integrations:** Support for AI workspaces (e.g., Grok, Anthropic) or cross-platform context transfer.
- **Extended functionality:** Browser extensions, mobile support, save output management—it's all on the table. The basic ChatCon implementation is just the beginning.

## Tips for Success
- **Keep PRs Small:** Focus on one feature or fix to simplify reviews.
- **Follow Token Guidelines:** Ensure saves respect ChatCon’s 500-token limit for `~hd` and ~200 for `~sc`.
- **Ask Questions:** Use Discussions or Issues if you’re unsure about implementation details.
- **Be Patient:** We’ll review contributions as quickly as possible, but thoroughness takes time.

## Questions?
Reach out via [Discussions](https://github.com/JohnChatConner/ChatCon/discussions) or open an [issue](https://github.com/JohnChatConner/ChatCon/issues). Thank you for helping make ChatCon the ultimate context-preserving powerhouse!