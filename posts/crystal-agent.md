# Crystal for Agents v1.20.0: Teaching LLMs to Write Better Crystal

April 17, 2026

A new project called "Crystal for Agents" just released version 1.20.0, syncing with Crystal's own versioning. The goal: help LLMs (like Gemini, Claude, or ChatGPT) generate correct, idiomatic Crystal code instead of Ruby-with-Crystal-syntax.

The maintainer, renich, noticed a common problem. LLMs tend to write Crystal as if it was Ruby. They ignore Crystal features like metaprogramming, use hashes when structs would be better, and sprinkle .not_nil! everywhere instead of trusting the type system.

The solution is a detailed text file (crystal.rst) that explains Crystal's features, fed to the LLM as context. The maintainer reports that after feeding this file, code quality improves dramatically and the .not_nil! habit disappears.

The forum discussion raises interesting counterpoints. Some developers find they don't need to teach LLMs about Crystal itself. Pointing them to the official API docs as a primary reference works well. When Crystal releases a new version, you just update the link rather than redrafting an entire guide.

Others argue that projects like this solve a real workflow problem: context drift. As a project grows, an LLM's knowledge of what was built and why degrades across sessions. A CHANGELOG, a Kanban board, and a session-start prompt that references both can keep the LLM grounded.

The discussion also touches on security tooling. In a project like Sysrift (a Crystal-based privilege escalation checker), type safety matters beyond style. A .not_nil! shortcut anywhere in a filesystem walker could be a runtime panic on an unexpected filesystem layout. The compiler catching type mismatches early means the tool handles edge cases correctly.

Whether you use Crystal for Agents directly or just link to API docs, the conversation highlights a growing reality. As LLMs become part of daily development, having good, fresh, Crystal-specific context is increasingly valuable. Projects like this are the first step toward making AI assistants genuinely helpful for Crystal programmers.

Links:

- Crystal for Agents repository (see the forum post for the link)
 [link](https://forum.crystal-lang.org/t/crystal-for-agents-v1-20-0-release/8889)
- Crystal Forum discussion thread
