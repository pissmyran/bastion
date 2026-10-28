# Plattformarna

Varje plattform är ett eget repo med egen kod, egna versioner och egen dokumentation. En plattform kan släppas utan att de andra påverkas.

| Repo | För | Byggd med | Länkar |
| --- | --- | --- | --- |
| [Bastion för Apple](https://github.com/pissmyran/bastion_apple) | iPhone, iPad, Mac och Apple TV | Swift, SwiftNIO SSH, SwiftUI | [Dokumentation](https://pissmyran.github.io/bastion_apple/) · [Releaser](https://github.com/pissmyran/bastion_apple/releases) |
| [Bastion för Linux](https://github.com/pissmyran/bastion_linux) | Linux-skrivbordet | Rust, GTK 4, libadwaita, VTE, russh | [Dokumentation](https://pissmyran.github.io/bastion_linux/) · [Releaser](https://github.com/pissmyran/bastion_linux/releases) |
| [Bastion för Windows](https://github.com/pissmyran/bastion_windows) | Windows | C#, .NET, WinUI, SSH.NET | [Dokumentation](https://pissmyran.github.io/bastion_windows/) · [Releaser](https://github.com/pissmyran/bastion_windows/releases) |
| [Bastion för Android](https://github.com/pissmyran/bastion_android) | Android | Kotlin, Gradle, Apache MINA SSHD | [Dokumentation](https://pissmyran.github.io/bastion_android/) · [Releaser](https://github.com/pissmyran/bastion_android/releases) |

## Vad som delas

- **Synkformatet.** Apple, Linux och Windows läser och skriver samma format för värdlistan; se [Synkformat](synkformat.md).
- **Reglerna.** Alla repon följer [STYRNING.md](https://github.com/pissmyran/.github/blob/main/STYRNING.md) i `pissmyran/.github`.
- **Granskningen.** Alla repon ärver den centrala CodeRabbit-konfigurationen i [pissmyran/coderabbit](https://github.com/pissmyran/coderabbit).

## Vad som inte delas

- **Kod.** Det finns ingen gemensam kodbas. Swift-kärnan SSHCore används bara av Apple-apparna; de andra plattformarna har egna implementationer.
- **Versioner.** Varje repo har egna taggar. `v1.0.0` för Linux säger ingenting om Windows.
