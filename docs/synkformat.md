# Synkformat

Apple-, Linux- och Windows-apparna kan synka värdlistan och snippets. De läser och skriver samma format, så att en lista som sparats på en plattform kan läsas på en annan.

## Källan

[Bastion för Apple](https://github.com/pissmyran/bastion_apple) äger formatet. Swift-modellerna i `Sources/SSHCore/` (`Host`, `HostStore`, `Snippet`, `SyncEngine` och `SyncCrypto`) definierar det, och fixturerna i [`Tests/fixtures/`](https://github.com/pissmyran/bastion_apple/tree/main/Tests/fixtures) är kontraktet.

## Kopiorna

| Repo | Fixturerna | Läs mer |
| --- | --- | --- |
| [Bastion för Linux](https://github.com/pissmyran/bastion_linux) | `LinuxApp/tests/fixtures/` | [Synkformat](https://pissmyran.github.io/bastion_linux/synkformat/) |
| [Bastion för Windows](https://github.com/pissmyran/bastion_windows) | `WindowsApp/Bastion.Core.Tests/csharp-hosts-fixture.json` | [Synkformat](https://pissmyran.github.io/bastion_windows/synkformat/) |

Bastion för Android har ännu ingen synk. När den byggs ska den följa samma format och testa mot egna kopior av fixturerna.

## När formatet ändras

1. Ändringen görs i Bastion för Apple: modellen och fixturen i samma PR.
2. Ett issue skapas i varje berört plattformsrepo med länk till PR:en.
3. Plattformarna kopierar de nya fixturerna och uppdaterar sina läsare och skrivare.
4. En fixtur ändras aldrig bara för att få ett test grönt.

Hela rutinen står i [Synkformat för Apple](https://pissmyran.github.io/bastion_apple/synkformat/).
