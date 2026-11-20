---
name: voxstudio-cloud-connect
description: Connect or troubleshoot the VoxStudio Web Cloud MCP in Cursor or another OAuth-capable agent. Use for setup, authentication, missing tools, or the Cloud session workspace.
---

# Connect VoxStudio Cloud

Use the Streamable HTTP endpoint `https://voxstudio.me/cloud/mcp`. In Cursor, use VoxStudio **Settings → MCP → Cursor** or merge this entry into the existing MCP configuration.

```json
{"mcpServers":{"voxstudio-cloud":{"url":"https://voxstudio.me/cloud/mcp"}}}
```

Reuse an existing entry for this URL. Let the user complete sign-in and consent in the browser. Check that the client reconnects and exposes the Cloud tools in the current chat. Restart the chat or reload the server if the client has a stale tool list.

Use the live catalog to resolve host prefixes. For example, the Cloud wire name `voxstudio_knowledge_list_sources` can have a server prefix in Cursor. Use `voxstudio_knowledge_list_sources` with a small `limit` to check read access without changing the library. Use `voxstudio_workspace` with an empty object when the user wants to open the Cloud reader in an MCP Apps-capable host.

Diagnose transport, OAuth and tool visibility separately. Ask the user to authenticate when the server indicates expired, missing or insufficient authorization. Keep credentials out of prompts, files and logs. Keep Cloud IDs and upload grants on the Cloud connection.
