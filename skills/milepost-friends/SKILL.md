---
name: milepost-friends
description: Catch up on visible friends’ Milepost Roadbooks and, when the user requests it, post or remove reactions and leave comments.
---

Use `get_friends_feed` to paginate the latest 100 visible Roadbooks. Use `get_friend_drive` for a specific drive's summary and note, and `get_drive_social` for comments and reactions. The server rechecks current friendship, visibility, blocks, moderation, and sharing preferences. Do not attempt to work around unavailable or private drives.

Feed and social timestamps use seconds since 2001-01-01 UTC; feed distance is meters and duration is seconds. Summarizing a feed does not mark it seen.

Read `get_drive_social` and choose a kind from its `reactionChoices` before calling `set_drive_reaction`. Each Roadbook offers heart, laugh, lightning, and three personalized emoji. Historical `racecar`, `checkeredFlag`, and `mountain` kinds remain supported for earlier reactions. Changed reactions notify the owner; repeating the same reaction does not. `remove_drive_reaction` removes only the connected user's reaction without a notification.

`add_drive_comment` posts 1–1000 characters as the connected user and notifies the owner when commenting on a friend's drive. Post only comments authorized by the user's request. Reading or catching up is not permission to interact. Comments are not idempotent: after an uncertain response, inspect `get_drive_social` before retrying, and stop if you cannot determine whether the comment already exists.

Reads need `social:read`; reactions and comments need `social:write`. Missing permission needs a new approval. A draft or visibility change may remove access between calls; report that without revealing cached private details.
