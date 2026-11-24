# MapleStory WZ dumps

JSON dumps of MapleStory client data files (`Data/*.wz` and `Data/Packs/*.ms`), one JSON file per `.img`.

## Layout

```
<server>/<client version>-<dump date>/<wz path>/<name>.img.json
```

| Folder | Server | Client version | Dumped |
|---|---|---|---|
| `classic/1.1.0.0-20261030` | MapleStory Classic World | 1.1.0.0 | 2026-10-30 (no canvas properties) |
| `classic/1.1.0.0-20261108` | MapleStory Classic World | 1.1.0.0 | 2026-11-08 |
| `classic/1.1.0.0-20261118` | MapleStory Classic World | 1.1.0.0 (after the 2026-11-18 patch; exe version unchanged) | 2026-11-18 |
| `classic/1.1.0.0-20261124` | MapleStory Classic World | 1.1.0.0 (after the 2026-11-24 minipatch; exe version unchanged) | 2026-11-24 |
| `gms/v272-20261121` | Global MapleStory | 8.272.3.0 (v272) | 2026-11-21 |

Each version folder has a `dump_log.txt` listing every source file, its WZ version and how many images were read.

## What's in it

- Every property tree except graphics and sound. These folders are skipped: `_Canvas`, `Character/Hair`, `Character/Face`, `Effect`, `UI`, `Sound`, `Morph`, `Map/Back`, `Map/Obj`, `Map/Tile`.
- Canvas nodes are kept as `{"_canvas": true, ...}` with their properties (`origin`, `lt`, `rb`, `delay`, ...) but no
  pixels; sound nodes as `{"_sound": true}`. The 2026-10-30 Classic dump has no canvas properties.
- Map files hold `info`, `foothold`, `ladderRope`, `portal`, `life`, `reactor`, `seat`, `miniMap` and the rest.

## Known gaps

`gms/v272-20261121`: 5 images failed to parse (string blocks of an unknown type):
`Mob/BossPattern/BalanceSettings/BalanceSettings_BossBellona.img`, `BalanceSettings_BossMaerin.img`,
`Mob/BossPattern/PatternPreset.img`, `Skill/Recipe_9200.img`, `Skill/Recipe_9201.img`.

## Notice

MapleStory and its game data are © NEXON. This repository is an unofficial reference for players and tool makers and
is not affiliated with or endorsed by NEXON.
