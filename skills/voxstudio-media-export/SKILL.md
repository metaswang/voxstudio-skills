---
name: voxstudio-media-export
description: Preview an existing VoxStudio Cloud media session, inspect transcript context or saved quotes, and export a transcript, subtitles, or audio.
---

# Inspect and export a Cloud session

Use the live tool schemas at `https://voxstudio.me/cloud/mcp`. Resolve the session using an ID returned by VoxStudio or provided by the user. If starting with a recording title, look it up through Cloud knowledge and verify the actual media `session_id`. Use `voxstudio_session_get` to confirm the session and its processing state.

- For playback, call `voxstudio_media_preview_url` with `session_id` and the desired `media` type. A video preview is available only for sessions that have the corresponding media.
- For transcript context, call `voxstudio_transcript_context` with `session_id` and `start_s`, and use `end_s` for a bounded range. For saved quote snapshots, call `voxstudio_session_list_quotes` and preserve any returned verification status.
- Call `voxstudio_session_export` with `session_id`, the requested `content` and a compatible `format`. The Cloud export schema covers transcript, subtitle and audio. Common combinations are transcript/TXT, subtitle/SRT or VTT, and audio/MP3, M4A or WAV. Use the available original, translation, bilingual or dub variant when the user asks for it.

Use explicit session status and the returned result to distinguish a ready export from pending or unavailable content. Return the requested signed link to the user and keep it out of public artifacts.
