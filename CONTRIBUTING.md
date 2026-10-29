# Contributing to Bastion

Thanks for wanting to contribute.

This repo is the Bastion hub and holds no code.

## Where a change belongs

- **Code and platform documentation:** in the platform's repo: [Apple](https://github.com/pissmyran/bastion_apple), [Linux](https://github.com/pissmyran/bastion_linux), [Windows](https://github.com/pissmyran/bastion_windows) or [Android](https://github.com/pissmyran/bastion_android).
- **The sync format:** in [Bastion for Apple](https://github.com/pissmyran/bastion_apple), which owns it.
- **The hub site and shared documentation:** here.

## Reporting

- **Bugs and requests:** open an issue with the matching form.
- **Security problems:** follow [SECURITY.md](SECURITY.md). Never publish vulnerability details in an issue, pull request or discussion.

## Workflow

1. Start from the latest `main` and work on your own branch.
2. Keep the change small and focused.
3. Build the site locally: `pip install --upgrade zensical` and `zensical build --strict`.
4. Open a pull request against `main` with a title that follows Conventional Commits, for example `fix: …`.
5. Let the reviews and checks turn green before merging.

Everything is written in English: code, comments, documentation, commit messages and pull requests.

## Sensitive information

Never commit passwords, tokens, keys, personal data or other secrets, and never put them in issues, pull requests or screenshots. If something leaks by mistake, treat it as compromised and rotate it.

## License

By contributing you confirm that you have the right to submit the change. Contributions are covered by the repository's license.
