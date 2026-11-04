# Ask Lums

Ask Lums is an LLM-powered assistant on [Olumide Olusesi's portfolio](https://olumideolusesi.com). Visitors can ask about my projects, experience and design approach instead of searching through every case study.

## How it works

The Next.js API route loads a curated set of Markdown documents covering my resume, project experience, methods, design philosophy and colleague feedback. It supplies these documents as context to Claude alongside the conversation history and streams the answer back to the interface.

The prompt instructs the model to ground answers in that context. When it cannot answer, it returns a marker that the server removes from the visible response. The server records the conversation in PostgreSQL and can send a follow-up notification for the unanswered question. A basic in-memory rate limiter reduces rapid repeated requests.

## Implementation

- Next.js API route and React interface
- Anthropic SDK for Claude and streamed text responses
- Curated Markdown context and multi-turn conversation history
- PostgreSQL conversation records and email follow-up integration

[API route source excerpt](source/ask-lums-route.js)

## Scope of this repository

This is a project write-up with a source excerpt from the portfolio application, not a standalone installable application. The private knowledge documents, database contents, credentials, email service implementation and the rest of the portfolio are excluded. The excerpt retains its original application imports; it needs the parent application's modules and configuration to run.

The fallback marker depends on model behavior and is not a guarantee against unsupported answers. The in-memory limiter resets with the server process. The source documents implementation, not an independently verified live service guarantee.
