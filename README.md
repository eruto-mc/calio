# Calio（eruto-mc の fork）

上流: [EdwinMindcraft/calio](https://github.com/EdwinMindcraft/calio)
／ 当部の枝 `eruto/world3-1.20.1`（上流の `1.20.x/forge` の `d54743e` から）
／ ライセンスは上流に従う。

この枝は、[eruto-mc/eruto-origins](https://github.com/eruto-mc/eruto-origins) の submodule として建てる（単体では建てない）。

## 当部が変えたこと

| コミット | 何を | なぜ |
| - | - | - |
| `93d80b3` | 登録データの読み解き（Netty のスレッド）・表への書き込み（メインスレッド）・`calio$getOrCreateHolderOrThrow` を、1 つの鍵 `CalioDynamicRegistryManager.SYNC_LOCK` で囲った | ログインで登録データを受け取るとき、2 つのスレッドが同じ表（鍵の無い `HashMap`）へ同時に書き、およそ 100 回に 1 回 `UnitListCodec` の NullPointerException で入れなかった |
