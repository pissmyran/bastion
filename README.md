# Bastion

**Documentation:** [pissmyran.github.io/bastion](https://pissmyran.github.io/bastion/)

Bastion is an SSH client for several platforms. Each platform has its own repo with its own code, versions and documentation. This repo is the hub: it gathers the links, describes what is shared and takes issues that concern every platform.

## The platforms

| Repo | For | Built with | Documentation |
| --- | --- | --- | --- |
| [Bastion for Apple](https://github.com/pissmyran/bastion_apple) | iPhone, iPad, Mac and Apple TV | Swift, SwiftNIO SSH, SwiftUI | [Documentation](https://pissmyran.github.io/bastion_apple/) |
| [Bastion for Linux](https://github.com/pissmyran/bastion_linux) | the Linux desktop | Rust, GTK 4, libadwaita, VTE, russh | [Documentation](https://pissmyran.github.io/bastion_linux/) |
| [Bastion for Windows](https://github.com/pissmyran/bastion_windows) | Windows | C#, .NET, WinUI, SSH.NET | [Documentation](https://pissmyran.github.io/bastion_windows/) |
| [Bastion for Android](https://github.com/pissmyran/bastion_android) | Android | Kotlin, Gradle, Apache MINA SSHD | [Documentation](https://pissmyran.github.io/bastion_android/) |

## Shared

- **The sync format** for the host list is shared by the platforms that sync. The source is the Swift models in [Bastion for Apple](https://github.com/pissmyran/bastion_apple); the other repos test against copies of the fixtures from there.
- **The project** [Bastion](https://github.com/pissmyran/bastion/projects) gathers issues from all five repos in one view.
- **The rules** for working in every repo are in [STYRNING.md](https://github.com/pissmyran/.github/blob/main/STYRNING.md) (Swedish).

## Reporting

- **Bugs or requests for one platform:** open an issue in that platform's repo.
- **Anything that concerns every platform** (the sync format, shared documentation): open an issue here.
- **Security problems:** follow [SECURITY.md](SECURITY.md).

## History

Until October 2026 every platform lived in this repo. The old code remains in the Git history and in the releases up to v0.1.3.
