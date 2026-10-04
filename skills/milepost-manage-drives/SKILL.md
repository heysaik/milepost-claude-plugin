---
name: milepost-manage-drives
description: Review synced Milepost drives, edit titles, notes or vehicles, manage draft details, publish drafts, and change drive visibility when requested.
---

Use `list_drives` for the synced library and `list_drafts` for unpublished recordings. Paginate with `next_offset`. Offline-only data is unavailable until the device syncs.

Read `get_drive` before editing. It returns a `revision`, note, summary, and optionally a route when `include_route=true`. Distances are meters; durations are seconds. The route is limited to 500 points; disclose `route_sampled` when relevant.

- `update_drive`: set only the requested `title`, `note`, or `vehicle_id`. Resolve vehicles through `get_garage`. Empty notes clear text; existing photos and recorded routes are preserved. Do not fabricate locations or recorded driving statistics.
- `set_drive_visibility`: choose `private`, `friends`, or `public`. Public permits publicly accessible share links. Friends visibility still follows friendship, blocks, and the owner's sharing preferences. Unpublished drafts reject this action; choose visibility with `publish_draft` when publication is requested.
- `publish_draft`: explicitly choose visibility and promote an existing draft. Publishing a non-private draft may notify eligible friends. Editing or filling in details alone does not authorize publication or a wider audience.

Pass `drive_id` and `expected_revision` from `get_drive` for every mutation. On conflict, reread and reconcile the requested fields; do not blindly replace the revision and repeat an outdated edit. If a response is lost, read the drive to establish whether it committed. Drive edits are restricted to the owner. Never silently publish as a workaround for an unavailable operation.

Reads need `drives:read`; mutations need `drives:write`. A missing scope requires a new connection approval. Report only changes confirmed by a successful tool result.
