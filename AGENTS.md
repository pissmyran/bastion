# AGENTS.md – bastion

The hub for the SSH client Bastion: the hub site, shared documentation and issues that concern every platform. The repository holds no code. The code lives in [bastion_apple](https://github.com/pissmyran/bastion_apple), [bastion_linux](https://github.com/pissmyran/bastion_linux), [bastion_windows](https://github.com/pissmyran/bastion_windows) and [bastion_android](https://github.com/pissmyran/bastion_android).

Read the shared rules at the start of every session: [GOVERNANCE.md](https://raw.githubusercontent.com/pissmyran/.github/main/GOVERNANCE.md) and [BASTION.md](https://raw.githubusercontent.com/pissmyran/.github/main/BASTION.md).

## Read first

1. [docs/platforms.md](docs/platforms.md): how the repositories fit together.
2. [docs/sync-format.md](docs/sync-format.md): when sync is involved. The format itself changes in `bastion_apple`.

## Commands

```bash
pip install --upgrade zensical && zensical build --strict
```

## Rules

- **No code here.** Code, tests and platform documentation change in the platform repositories.
- **Links** to the platform repositories and their sites are in `README.md`, `docs/` and `.github/ISSUE_TEMPLATE/config.yml`. If a repository is renamed, update all three.
- **The site is published on GitHub Pages only when a release is created.** A site change that should go out needs `feat:` or `fix:` in the title. The release gate is `.github/release-required-checks` (`Analyze (actions)`).
- **`site_url`** in `zensical.toml` is a custom domain, while the repository's homepage is `pissmyran.github.io/bastion`. Do not change `site_url` without the owner's decision.
- **Extra care:** links to the platform repositories and the release gate.
