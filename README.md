# NKeeper plugin catalog

`catalog.json` lists the plugins NKeeper servers can install and upgrade from GitHub (NKeeper's `docs/architecture.md` §9.1). Servers read it from this repository's `main` branch.

Each entry names a plugin's ID and the repository whose releases carry it:

```json
{ "id": "kvm", "repository": "OpenCraft-Solutions/NKeeper-Plugin-KVM", "summary": "One line for the plugins page" }
```

- **Versions aren't listed here.** A server finds them in the repository's releases: tag `v<version>`, with `<id>-<version>.nkp` and its `.sha256`. Releasing a plugin needs no change to this file.
- **Editing this file changes nothing on a server until it refreshes** (daily, on **Check for updates**, or `sudo nkeeper plugin update`). Installing and upgrading stay separate steps, as `apt update` and `apt upgrade` are.
- **Listing isn't trusting.** A server installs a package only if it verifies: an official plugin needs NKeeper's official signing key, and a third-party one needs a key the server's root trusts for its ID.

Protect this repository as you would a plugin's: whoever can change it decides which repository each ID comes from.
