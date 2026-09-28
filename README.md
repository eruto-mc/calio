> ## ⚠ これは改変版です（EdwinMindcraft/calio の fork・公式のものではありません）
>
> **This is a modified version of Calio (Forge port), not the official build.**
> Modified by the minecraft club (eruto). Original work: [EdwinMindcraft/calio](https://github.com/EdwinMindcraft/calio)
> (itself a port of [apace100/calio](https://github.com/apace100/calio)).
> Licensed under **MIT**, same as upstream. The original authors do not endorse this build.
>
> 上流: [EdwinMindcraft/calio](https://github.com/EdwinMindcraft/calio) ／ 枝 `eruto/world3-1.20.1`
> ／ 上流の枝 `1.20.x/forge` の `d54743e` から分岐（上流には README が無い）。
> この枝は [eruto-mc/eruto-origins](https://github.com/eruto-mc/eruto-origins) の submodule として建てる（単体では建てない）。
>
> ⚠ **不具合をここの改変版で見つけても、上流へ報告しないでください。**
>
> **当部が変えたところ**（中身は `git log --author=erutobusiness`）:
>
> | 何を | なぜ |
> | - | - |
> | 登録データの読み解き（Netty のスレッド）・表への書き込み（メインスレッド）・`calio$getOrCreateHolderOrThrow` を、1 つの鍵 `CalioDynamicRegistryManager.SYNC_LOCK` で囲った | ログインで登録データを受け取るとき、2 つのスレッドが同じ表（鍵の無い `HashMap`）へ同時に書き、およそ 100 回に 1 回 `UnitListCodec` の NullPointerException で入れなかった |
