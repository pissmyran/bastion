# Bastion

**Dokumentation:** [pissmyran.github.io/bastion](https://pissmyran.github.io/bastion/)

Bastion är en SSH-klient för flera plattformar. Varje plattform har ett eget repo med egen kod, egna versioner och egen dokumentation. Det här repot är navet: det samlar länkarna, beskriver det som är gemensamt och tar emot ärenden som gäller alla plattformar.

## Plattformarna

| Repo | För | Byggd med | Dokumentation |
| --- | --- | --- | --- |
| [Bastion för Apple](https://github.com/pissmyran/bastion_apple) | iPhone, iPad, Mac och Apple TV | Swift, SwiftNIO SSH, SwiftUI | [Dokumentation](https://pissmyran.github.io/bastion_apple/) |
| [Bastion för Linux](https://github.com/pissmyran/bastion_linux) | Linux-skrivbordet | Rust, GTK 4, libadwaita, VTE, russh | [Dokumentation](https://pissmyran.github.io/bastion_linux/) |
| [Bastion för Windows](https://github.com/pissmyran/bastion_windows) | Windows | C#, .NET, WinUI, SSH.NET | [Dokumentation](https://pissmyran.github.io/bastion_windows/) |
| [Bastion för Android](https://github.com/pissmyran/bastion_android) | Android | Kotlin, Gradle, Apache MINA SSHD | [Dokumentation](https://pissmyran.github.io/bastion_android/) |

## Gemensamt

- **Synkformatet** för värdlistan delas av plattformarna som synkar. Källan är Swift-modellerna i [Bastion för Apple](https://github.com/pissmyran/bastion_apple); de andra repona testar mot kopior av fixturerna därifrån.
- **Projektet** [Bastion](https://github.com/pissmyran/bastion/projects) samlar ärenden från alla fem repona i en vy.
- **Reglerna** för arbetet i alla repon står i [STYRNING.md](https://github.com/pissmyran/.github/blob/main/STYRNING.md).

## Rapportera

- **Fel eller önskemål för en plattform:** skapa ett issue i plattformens repo.
- **Sådant som gäller alla plattformar** (synkformatet, gemensam dokumentation): skapa ett issue här.
- **Säkerhetsproblem:** följ [SECURITY.md](SECURITY.md).

## Historik

Fram till oktober 2026 låg alla plattformar i det här repot. Den gamla koden finns kvar i Git-historiken och i releaserna upp till v0.1.3.
