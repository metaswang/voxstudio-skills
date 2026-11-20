---
name: voxstudio-voiceover
description: Find VoxStudio Cloud voices and turn supplied text into a downloadable voiceover with the requested language and voice.
---

# Generate a voiceover

Use the live schemas on the VoxStudio Cloud MCP at `https://voxstudio.me/cloud/mcp`.

1. Call `voxstudio_dub_reference_list` with `read_lang` for the script language. Use `scope: "public"` for public presets or the requested accessible custom voice. Use a returned reference ID. If the user wants to choose between candidates, present the available names and previews before submitting.
2. Call `app_dubbing` with the supplied `text`, the requested `language` and the selected `reference_audio_id`. Set format or speed only when needed. The schema accepts 1–12,000 characters per request.
3. Poll `voxstudio_dub_result` using the exact returned `session_id` until the job reaches a terminal state. If submission outcome is unclear, recover that job before submitting again.
4. On success, offer the returned playback URL or use `voxstudio_session_export` with `content: "audio"` and the requested supported format. Treat signed URLs as temporary and share them only with the requesting user.
