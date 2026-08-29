# QuestPlates

## Repository Workflow

- The GitLab project under `rgxmods/warcraft` is authoritative. Normal work belongs on task branches and must merge through GitLab merge requests, never directly to the default branch.
- Shared CI is included from `rgxmods/warcraft/RGX-Framework` at `/.gitlab/ci/addon.yml`; validation must pass before publishing to the configured downstream GitHub repository.
- The configured downstream GitHub repository is for distribution, not development authority.
- Keep GitLab and GitHub release tags identical, and use protected GitLab release tags.
- Preserve any existing working Wago connection and ID exactly. Never create a new Wago connection without explicit user direction.
- Publishing integrations prohibited by the shared validation policy are retired and must not be restored.
- The root `README.md` must remain detailed and project-specific. Narrow distribution edits must not replace or truncate installation, features, compatibility, usage, media, maintenance status, or support content.
- Verify relative README assets. Do not overwrite newer compatibility or maintenance facts with stale monorepo or history text.
