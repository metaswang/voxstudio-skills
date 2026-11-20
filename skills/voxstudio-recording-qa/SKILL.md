---
name: voxstudio-recording-qa
description: Answer questions about VoxStudio Cloud recordings using original transcripts and citations. Use to find sessions, compare recordings, locate exact quotes, or count authorized sources.
---

# Answer from recording evidence

Use the VoxStudio Cloud MCP at `https://voxstudio.me/cloud/mcp` and take argument definitions from its live tool schemas.

- Use `voxstudio_knowledge_list_sources` for literal title lookup and to page a source directory. Use `voxstudio_knowledge_aggregate` for full-inventory counts or groups.
- Use `voxstudio_knowledge_search` for topical or semantic discovery. Use `voxstudio_knowledge_find_text` to locate literal text in an identified source. Search results are candidates.
- Use `voxstudio_knowledge_fetch` with a returned source or evidence ID and `material: "canonical"` to verify wording in the original. Read around the relevant passage for context. Follow `next_cursor` or bounded ranges when the claim requires full coverage. Use `voxstudio_knowledge_methods` when you need the service's published research method.

If the host supports the evidence workspace and the user wants a traceable question in it, call `app_knowledge` with `action: "begin"`, the question and a fresh UUID `request_id`. Supply the returned `workspace_id` and `turn_id` together on evidence calls. Finish with `knowledge_complete_turn` using a fresh request ID for that operation and cite only IDs this turn successfully observed. Preserve request IDs across retries. For ordinary chat, evidence calls can omit both workspace fields.

Compose the answer from verified passages. Cite the source title and any returned locator or timestamp. Preserve wording in direct quotes and state which sources were checked if evidence is missing. A knowledge source ID and a media session ID have distinct purposes. Use a real returned media session ID for media operations.
