---
name: voxstudio-transcribe
description: Transcribe a user-provided audio or video file in VoxStudio Cloud, optionally translate subtitles, and monitor the job until its output is ready.
---

# Transcribe or translate media

Use the live schema for `app_transcription` from the VoxStudio Cloud MCP at `https://voxstudio.me/cloud/mcp`.

- For an HTTPS attachment, use `action: "submit"` with `media_file.download_url` and the attachment's `media_file.file_id`. Include MIME type and filename if known.
- For a local file, call `action: "prepare"` with `file_name` and `mime_type`. PUT that file's bytes to the returned `upload.signed_url` with the returned headers. After the PUT succeeds, follow the returned continuation, using `action: "complete"` and the exact `session_id`. Use a client that can transfer bytes directly to the signed URL. Keep that URL and its headers private.

Set requested processing options on submit or prepare. Omit `language_hint` for automatic detection. Use `target_language` when translation is requested. Clip bounds are milliseconds. Give the service accurate media metadata when available.

Follow `next_call` and check `voxstudio_session_get` on that session until terminal. Check any known session before retrying an ambiguous submission. Report the actual job status and any error returned. For a completed transcript, read a bounded interval with `voxstudio_transcript_context` or use `voxstudio_session_export` for the requested transcript or subtitle format.
