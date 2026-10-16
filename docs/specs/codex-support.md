# Codex marketplace support
Status: Verified
Signed off: —

## Problem and scope
Codex users need to discover and install the same five official plugins.
Existing Mind, Claude Code and Augment manifests remain compatible.

## Requirement
- REQ-CODEX-001: Codex discovers and installs every catalogued plugin, with
  reusable skills available after installation, including Butler's greeting.
  Acceptance: Codex lists all five names and installs each without errors.

## Design and failure behavior
Add `.agents/plugins/marketplace.json` with local plugin sources and explicit
installation/authentication policies. Add `.codex-plugin/plugin.json` to each
plugin, referencing its existing skills directory. Butler gains a greeting
skill matching its existing command. No tools, hooks or services are added.
Failed installation is reported by Codex; existing clients keep their manifests.

## Rollout and rollback
Publish through main; users add the marketplace and choose plugins with the CLI.
Remove installed plugins with `codex plugin remove NAME@mindcode-plugins-official`
and remove the marketplace with `codex plugin marketplace remove
mindcode-plugins-official`. Revert this change to withdraw Codex packaging.
No scheduled compute or additional CI jobs are introduced.

## Traceability and verification
REQ-CODEX-001 maps to the Codex catalog, five compatibility manifests, Butler
skill and README instructions. Verify catalog/manifest/path consistency,
existing FME tests, Codex discovery and installation in an isolated profile,
and installation from merged main into the user's profile.

Reference: https://developers.openai.com/plugins/build/plugins

## Verification evidence
- Catalog/manifest/path consistency: all five plugins valid, 19 skills.
- `uv run --with pytest python -m pytest plugins/fme/tests -q`: 32 passed.
- `codex plugin marketplace add /private/tmp/mindcode-plugins-codex-work --json`:
  registered successfully; `plugin list --available --json` found all five.
- `codex plugin add NAME@mindcode-plugins-official --json`: all five installed
  successfully into the user cache. This uses the actual local profile rather
  than a separate test profile, fulfilling the requested local installation.
- `git diff --check`: passed.
