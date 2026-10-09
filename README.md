# effectcraft-snap

Snap packaging for [EffectCraft](https://getartcraft.com/apps/effectcraft), a motion graphics and visual effects compositor,
from the open-source [ArtCraft](https://getartcraft.com/) Crafting Apps.
Upstream: <https://github.com/storytold/effectcraft>.

The snap repackages the official upstream Linux release tarball
(checksum-verified against the release's `SHA256SUMS.txt`) for amd64 and arm64.

```sh
sudo snap install effectcraft
effectcraft          # desktop app
effectcraft.cli      # headless CLI / MCP server
```

## Workflows

- **Build and publish** (`build.yml`): builds the snap on amd64 and arm64 for
  every push and pull request. Pushes to `main` release to `candidate`; a manual run
  can pick any channel (leave it empty to only build).
- **Check upstream release** (`check-upstream.yml`): runs every 6 hours, and when
  a newer upstream release exists it bumps `version` in `snap/snapcraft.yaml`,
  commits to `main` and releases a new build to `candidate`.

## Setup

1. Register the name: `snapcraft register effectcraft`.
2. Export store credentials and save them as the `STORE_LOGIN`
   repository secret:
   `snapcraft export-login --snaps effectcraft --channels edge,candidate,beta,stable --acls package_access,package_push,package_release -`
