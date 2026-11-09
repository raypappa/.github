# Shared GitHub configuration

This repository contains shared GitHub configuration and automation for the `raypappa` repositories.

## Repository labels

Label definitions live in `.github/labels/`. The shared blueprint includes the common labels, while each repository file adds any labels specific to that repository. Label Blueprint applies the matching file to the corresponding repository.

The workflow previews changes for pull requests and does not prune labels. Pushes to `main` apply the blueprint; manual runs default to preview and can be explicitly set to sync.

### GitHub App setup

Before previews or syncs can call the target repositories, configure these repository-level Actions settings:

- Variable `APP_CLIENT_ID`: the Client ID of the `raypappa-sasha` GitHub App.
- Secret `APP_PRIVATE_KEY`: the App's private key.

Install the App on `homelab`, `hermes-agent-manager`, `mcp-meetup`, `prints-catalog`, and `safeway-coupons` with the repository permission **Issues: read and write**. The workflow requests a token scoped to one target repository at a time, with only Issues write permission. The App does not need access to this central repository for label syncing.
