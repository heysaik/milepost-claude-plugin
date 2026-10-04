---
name: milepost-manage-profile
description: View and edit the connected Milepost profile when users ask to check their handle, change their display name, update their bio, or rename their handle.
---

Use `get_profile` to resolve the connected account. `update_profile` changes only supplied `display_name`, `bio`, or `handle`; an empty bio clears it. Handles are normalized and must be unique. A handle change also changes the public profile URL. Do not infer new profile text or a handle from unrelated conversation.

Profile edits need `profile:write`; reads need `profile:read`. Existing connections may need a new approval for added permissions. Linking uses the user's Milepost handle and sends approval notifications to registered devices. Never request iCloud Keychain credentials, device tokens, or passwords. The approval screen opens from the notification.
