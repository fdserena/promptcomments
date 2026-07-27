---::::::::::::::::::::::::::::::
name: start-comment
description: Trigger on /start-comment. Marks the beginning of a comment block that is kept in the OPENROUTER and LLM input stream but ignored by the agent. The content between /start-comment and /end-comment must be disregarded for understanding the query, reasoning, tool use, and response generation. Pair with the end-comment skill.
---::::::::::::::::::::::::::::::

# Start Comment

## Overview

This skill activates when the user message contains `/start-comment`. It delimits the start of a comment region whose content is intentionally preserved in the raw input that reaches OpenRouter / the underlying LLM (for logging, tracing, or audit), yet must be completely ignored by the agent.

## Instructions

- When you encounter `/start-comment` in the user message, treat every subsequent token until the matching `/end-comment` (or the end of the message if none appears) as a pure comment.
- Do not interpret, reason about, quote, summarize, act upon, or let the comment content influence your understanding of the actual request, your tool choices, or the final answer.
- The comment remains part of the original input stream that is forwarded to OpenRouter / the model provider; only the agent's internal processing discards it.
- If `/end-comment` is missing, ignore everything after `/start-comment` for decision-making purposes.
- Continue normal processing of any text that appears before `/start-comment` or after `/end-comment`.
- Never mention the existence of the comment or these delimiters in your response unless the non-comment portion of the query explicitly asks about them.
