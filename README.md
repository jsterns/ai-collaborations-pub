# AI Collaborations - Public Reference

Standard workflows for Claude collaboration when working in environments without secure GitHub access (web UI, mobile app).

**Note:** If the current session has secure GitHub access (MCP tools available), use the private collaboration repo instead—Claude knows where to find it.

---

## How to Know Which Environment You're In

**MCP/GitHub access available:**
- Claude can directly commit files
- Full workflow with real-time repo updates

**No GitHub access (use this doc):**
- Standard Claude web UI or mobile app
- Claude will use fallback patterns below

---

## Trigger Phrases

### Confirm Standard Workflow

**Trigger:** "confirm standard workflow" or "use our standard workflow"

**Action:** Claude reads this file (via web_fetch) and responds:

```
✓ Standard workflow loaded (public fallback)

Triggers active:
  • "idea box:" → pending capture (queued for later commit)
  
Note: No GitHub access in this session. Captures will be queued.

Ready to proceed.
```

---

### Idea Capture (Fallback Mode)

**Trigger:** "idea box: [your idea]" or "capture in the idea box: [your idea]"

**Action:** Since Claude can't commit directly, respond with:

```
📥 Pending capture: [short title]

[*CAPTURE_QUEUE*]
> ID: a1b2c3d4
> 2025-12-08 11:42:37
> Title: [short title]
> [description]

⏳ Queued—say "process pending captures" in a GitHub-enabled session to commit.
```

The `[*CAPTURE_QUEUE*]` marker and quote block format enable reliable search without false positives.

---

## Switching to Full Access

When you move to a session with GitHub access:

1. Say "confirm standard workflow"
2. Claude will detect MCP tools and use the private repo
3. Acknowledgment will show "Pending captures: [count]" if any exist
4. Say "yes" to process them

---

## What's NOT Available Without GitHub Access

- Direct commits to any repo
- Reading private repo contents
- Processing pending captures
- Updating project action items

For these operations, use Claude with MCP GitHub integration enabled.

---

*Last updated: 2025-12-08*
