# Build Night: The Data Layer for Agentic Apps

**pgEdge + Constructive · AngelList, San Francisco · June 23, 2026**

Welcome. This is your prep page. Skim it before you arrive so the 60-minute build block is spent building, not installing. Everything here is optional, but the more you set up in advance, the more you'll ship on the night.

The theme: moving agents from demos into production, where they read, write, remember, and act on real data. We'll be building on the **pgEdge Agentic AI Toolkit for Postgres**: distributed Postgres, agent-native database access via the MCP Server, hybrid search (VectorChord-bm25 + pgvector), and a turnkey RAG Server.

---

## Get the toolkit

- **pgEdge AI Toolkit:** https://www.pgedge.com/download/ai-toolkit
- **pgEdge Enterprise Postgres:** https://www.pgedge.com/download/enterprise-postgres

## The repos you'll be working from

- **Postgres MCP Server** — agent-native database access: https://github.com/pgEdge/pgedge-postgres-mcp
- **RAG Server** — turnkey hybrid-search RAG over Postgres: https://github.com/pgEdge/pgedge-rag-server
- **Postgres images** — the pgEdge Enterprise Postgres Docker images (pgvector + VectorChord-bm25 built in): https://github.com/pgEdge/postgres-images

---

## Recommended setup

You don't need to build the whole stack ahead of time. The pgEdge quickstarts get you running with minimal effort, and each of the build prompts below points at the right one.

**The fastest way to get something real on your screen** is the MCP Server quickstart: one command brings up Postgres with the Northwind sample dataset, the MCP Server, and a natural-language web UI. From there you can ask questions over live data, make governed writes, or point Claude Code at it. Start here if you're not sure which prompt you want.

If you'd rather come in cold and build live on the night, that works too. Clone the repos above, have Docker running, and we'll walk the architecture in the first 15 minutes before the build block starts.

---

## Before you arrive

A few minutes of prep here saves you from burning your build block on downloads over venue wifi.

**Docker.** Have Docker Desktop (or Docker Engine + Compose) installed and running. Do a quick `docker run hello-world` to confirm it works.

**Pull the images ahead of time.** This is the single most useful thing you can do in advance. Conference wifi plus 100 people pulling multi-gigabyte images at once is the classic time-killer. Clone whichever quickstart you plan to use and run its pull/setup step the night before, at home or on good wifi, so the images are already cached on your laptop.

**LLM provider — pick one:**

- **Anthropic API key (recommended default).** Works immediately, no local horsepower required. Bring your own key from https://console.anthropic.com. This is the path we'd suggest for most people.
- **Ollama (local, optional).** If your laptop can comfortably run a local model (recent Apple Silicon with 16GB+ of memory, or a machine with a capable GPU), Ollama lets you build fully offline with no API key. If you go this route, **pull your models before you arrive** (`ollama pull` for both a chat model and an embedding model), not on venue wifi. If you're not sure your machine can handle it, bring an Anthropic key instead.

**OS notes.** macOS (Apple Silicon and Intel), Linux, and Windows with WSL2 all work. The pgEdge images are multi-arch, so Apple Silicon runs natively. On Windows, run Docker through WSL2 for the smoothest experience. The Postgres container won't run as root, so don't override the container user.

**Editor / agent (optional).** If you want to drive the MCP Server from an agent, have Claude Code or Claude Desktop installed and ready.

---

## The four build prompts

Pick one, or bring your own agent-touching backend problem. These map to the suggested prompts from the event page.

### 1. Agent-native access to Postgres (MCP)

Point Claude Code or the natural-language web UI at the pgEdge MCP Server and have an agent introspect a real schema, answer questions over live data, and make governed writes. Structured database access with read-only enforcement and audited writes — no ORM, no glue code.

*Start from:* the MCP Server quickstart (Northwind + MCP + web UI).

### 2. Hybrid RAG on Postgres (RAG)

Stand up the pgEdge RAG Server over a corpus and ask it real questions. One pipeline fusing VectorChord-bm25 keyword ranking with pgvector semantic search — the retrieval layer living inside the database instead of a separate vector store.

*Start from:* the RAG Server quickstart.

### 3. Distributed Postgres, write anywhere (cluster)

Bring up a two-node active-active pgEdge cluster, load Northwind, then write to either node and watch the row appear on the other. Multi-master replication where every node takes writes — the write-anywhere data layer underneath multi-region agents.

*Start from:* the distributed Docker Compose example in the `postgres-images` repo.

### 4. Agent builds the app, then runs on it (wildcard)

Have Claude design and seed a schema through the MCP Server, then drop a minimal dashboard on top that talks to that same server for every read and write. The agent uses one MCP server to build the app, and the running app uses that same server at runtime, with zero bespoke DB code in between.

*Start from:* the MCP Server quickstart, then build outward.

---

## On the night

- **5:30** — Doors open. Lobster rolls, drinks, conversation.
- **6:10** — Welcome and opening remarks.
- **6:20** — Architecture walkthrough with pgEdge engineering.
- **6:30** — Build block. Pair up or build solo.
- **7:30** — Lightning demos from the room.
- **8:00** — Network and chill.

If you demo, your build can be featured in the post-event reference publication. There's a video team on-site and we'll share demo videos with you afterward.

See you there. Bring something you want to build.
