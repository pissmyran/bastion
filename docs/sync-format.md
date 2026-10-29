# Sync format

The Apple, Linux and Windows apps can sync the host list and snippets. They read and write the same format, so a list saved on one platform can be read on another.

## The source

[Bastion for Apple](https://github.com/pissmyran/bastion_apple) owns the format. The Swift models in `Sources/SSHCore/` (`Host`, `HostStore`, `Snippet`, `SyncEngine` and `SyncCrypto`) define it, and the fixtures in [`Tests/fixtures/`](https://github.com/pissmyran/bastion_apple/tree/main/Tests/fixtures) are the contract.

## The copies

| Repo | Fixtures | Read more |
| --- | --- | --- |
| [Bastion for Linux](https://github.com/pissmyran/bastion_linux) | `LinuxApp/tests/fixtures/` | [Sync format](https://pissmyran.github.io/bastion_linux/sync-format/) |
| [Bastion for Windows](https://github.com/pissmyran/bastion_windows) | `WindowsApp/Bastion.Core.Tests/csharp-hosts-fixture.json` | [Sync format](https://pissmyran.github.io/bastion_windows/sync-format/) |

Bastion for Android has no sync yet. When it is built, it must follow the same format and test against its own copies of the fixtures.

## When the format changes

1. The change is made in Bastion for Apple: the model and the fixture in the same PR.
2. An issue is opened in every affected platform repo with a link to the PR.
3. The platforms copy the new fixtures and update their readers and writers.
4. A fixture is never changed just to make a test pass.

The full routine is in [Sync format for Apple](https://pissmyran.github.io/bastion_apple/sync-format/).
