# The platforms

Each platform is its own repo with its own code, versions and documentation. A platform can be released without affecting the others.

| Repo | For | Built with | Links |
| --- | --- | --- | --- |
| [Bastion for Apple](https://github.com/pissmyran/bastion_apple) | iPhone, iPad, Mac and Apple TV | Swift, SwiftNIO SSH, SwiftUI | [Documentation](https://pissmyran.github.io/bastion_apple/) · [Releases](https://github.com/pissmyran/bastion_apple/releases) |
| [Bastion for Linux](https://github.com/pissmyran/bastion_linux) | the Linux desktop | Rust, GTK 4, libadwaita, VTE, russh | [Documentation](https://pissmyran.github.io/bastion_linux/) · [Releases](https://github.com/pissmyran/bastion_linux/releases) |
| [Bastion for Windows](https://github.com/pissmyran/bastion_windows) | Windows | C#, .NET, WinUI, SSH.NET | [Documentation](https://pissmyran.github.io/bastion_windows/) · [Releases](https://github.com/pissmyran/bastion_windows/releases) |
| [Bastion for Android](https://github.com/pissmyran/bastion_android) | Android | Kotlin, Gradle, Apache MINA SSHD | [Documentation](https://pissmyran.github.io/bastion_android/) · [Releases](https://github.com/pissmyran/bastion_android/releases) |

## What is shared

- **The sync format.** Apple, Linux and Windows read and write the same format for the host list; see [Sync format](sync-format.md).
- **The rules.** Every repo follows [STYRNING.md](https://github.com/pissmyran/.github/blob/main/STYRNING.md) in `pissmyran/.github`.
- **The review.** Every repo inherits the central CodeRabbit configuration in [pissmyran/coderabbit](https://github.com/pissmyran/coderabbit).

## What is not shared

- **Code.** There is no shared code base. The Swift core SSHCore is only used by the Apple apps; the other platforms have their own implementations.
- **Versions.** Each repo has its own tags. `v1.0.0` for Linux says nothing about Windows.
