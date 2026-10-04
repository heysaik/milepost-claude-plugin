---
name: milepost-manage-garage
description: View the connected Milepost garage, add a vehicle, rename a vehicle, or change the primary vehicle.
---

Read `get_garage` to resolve the exact vehicle and current revision. Ask when a vehicle is ambiguous. `add_vehicle` needs a caller-generated stable UUID, make, model, optional year/trim/color/nickname, and `expected_revision`. Reuse the UUID on a retry and check the garage after an uncertain response.

`update_vehicle` accepts a vehicle UUID, `expected_revision`, nickname and/or `make_primary=true`. Empty nickname clears it. Changing the primary vehicle affects future selections; it does not rewrite prior drives. These tools do not remove vehicles or change an existing vehicle's specifications.

On a revision conflict, reread the garage and reconcile the user's requested change. Do not invent trim specifications or purchase anything. Adding a vehicle automatically requests generic artwork in the background, subject to cache availability and generation limits. A successful garage save does not mean its image is ready; do not promise completed artwork or retry additions to force generation. Garage details can appear on the public profile and text is moderated. Reads need `garage:read`; mutations need `garage:write`. Report only confirmed changes.

For additions, make and model are required; year, trim and exterior `color` are optional. Omit details the user has not supplied rather than inventing them. Garage results use year `0` and empty color/trim strings for unspecified values.
