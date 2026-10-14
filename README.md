# DOSurvivors

A horde-survival roguelite that looks like MS-DOS. You are the blinking cursor, enemies are ASCII characters, your weapons are DOS commands and your upgrades are punctuation. Survive 10 minutes, then terminate the boss. Beat it and the run continues on `D:\`, then on the floppy `A:\`.

> **Proof of concept.** DOSurvivors is a test project, not a finished game. Balance, features and content may change or stay rough, and bugs are expected.

![DOSurvivors title screen](images/mainscreen.png)

## Play

**[Play in your browser](https://b4help.github.io/dosurvivors/)** (desktop or mobile).

DOSurvivors is a single `index.html` with no build step and no internet connection required.

- **Online:** the link above, hosted on GitHub Pages.
- **Locally:** download the repo and open `index.html` in a browser.
- **On a web server:** copy the folder to any static host.

Keep `Web437_IBM_VGA_8x16.woff` next to `index.html`. Without it the game falls back to Courier New and the box-drawing characters won't line up.

## Controls

| Action | Keyboard | Touchscreen |
|---|---|---|
| Move | WASD or arrow keys | On-screen stick in the bottom corner (switch left/right in the pause menu) |
| Pause (loadout and stats) | ESC or P | Tap the top or bottom bar |
| Pick an upgrade | 1-3, or W/S then ENTER, or click | Tap an option |
| Sound on/off | M | From the pause menu |
| Help | H on the title screen | Tap "Read HELP.TXT" |

The game detects touchscreens on its own, shows the stick and switches the on-screen hints to match. On phones held upright, the level-up and pause boxes use a narrower layout with bigger text.

## How it plays

Enemies swarm in from every side and your weapons fire on their own. Kills drop XP (`+`). Each level pauses the game and **SETUP.EXE** offers three choices: a new weapon, a weapon level or a driver. Every minute gets harder, with elites, fork bombs and tougher enemy types. At 10:00 every enemy is terminated and **FATAL.EXE** loads. Kill it to win.

![Gameplay](images/gameplay1.png)

## Drives

DOSurvivors has three drives, played in order as one run. Every run starts on **`C:\GAMES`**: survive 10 minutes and terminate **FATAL.EXE**. Beat it and the run continues on **`D:\`**, which is the same 10-minute shape with these changes:

- **Walls.** Small solid blocks scattered across the field, at most one per area and never joined into corridors. You, enemies and bullets can't cross them, and your shots stop at them. Walls are random every run.
- **New processes.** Trojan, keylogger and zip bomb (see below).
- **A new boss.** **CHKDSK.EXE**, with 45000 HP.
- **v2 weapons.** Once a weapon is maxed (level 7, on C:\ or during D:\), its v2 is offered as an upgrade. The v2 replaces the base weapon in the same slot, starts again at level 1 with the base weapon's max stats, and levels up to 7. Each v2 adds its own effect that grows at levels 2, 5 and 7:

| v2 | Effect |
|---|---|
| DIR2 | Listings split into subdirectory shards on impact (more shards as it levels) |
| TYPE2 | Printed text burns in and keeps hurting anything standing on it (longer burn) |
| COPY2 | Orbiting files launch copies of themselves outward (faster launches) |
| DEL2 | Processes deleted by the aura explode (bigger blast) |
| PING2 | Packets explode on impact (bigger, stronger blast) |
| TREE2 | Branches stun every process they strike (longer stun) |
| DEFRAG2 | Blocks pull nearby processes into the grinder (stronger pull) |
| FORMAT2 | A second verify pass follows every format (stronger verify pass) |

Beat **CHKDSK.EXE** and the run continues on **`A:\`**, a floppy disk:

- **A round arena.** The disk has an edge you can't cross, so there's nowhere to run.
- **5x the processes.** Spawn rate and on-screen count are five times higher. XP per kill is lower to match.
- **Bad sectors.** A new one appears every 22 seconds (up to 12). Standing in one drains 10 HP per second.
- **New processes.** Disk swap (`S`) blinks right next to you, head crash (`H`) locks on and charges, write-protect tab (`T`) takes only 25% damage from projectiles.
- **A new boss.** **FORMAT A:**, with 120000 HP. Bullet rings with a gap to slip through, aimed fans and head crash summons. Below half HP it adds a spiral and drops bad sectors where you stand.
- **Super weapons.** A 7th weapon slot that holds one super weapon, offered on level-up:

| Super weapon | What it does |
|---|---|
| DELTREE.EXE | Marks the densest swarm, then deletes the whole branch in one huge blast |
| XCOPY.EXE | Spinning copy beams sweep around you |
| FDISK.EXE | Partition lines sweep across the whole screen, hitting everything they cross |

Your weapons and drivers carry over from each drive into the next. Timed power-ups don't. There is no drive select: die anywhere and the next run starts again on C:\GAMES. Your best run on each drive is saved in your browser's localStorage. The save belongs to one browser and one address, so a copy of the game at a different address starts with a fresh save.

### Weapons

You start with DIR. Hold up to 6, each upgrades to level 7.

| Command | Effect |
|---|---|
| `C:\>DIR` | Fires `<DIR>` listings at the nearest enemy |
| `C:\>TYPE` | Types a DOS error message across the screen like a whip |
| `C:\>COPY` | Copied files orbit around you |
| `C:\>DEL` | Damage aura that deletes anything too close |
| `C:\>PING` | Homing packets |
| `C:\>TREE` | Branches strike a random target and chain between enemies |
| `C:\>DEFRAG` | Drops fragmented blocks that grind enemies |
| `C:\>FORMAT` | Periodic expanding ring that formats everything around you |

### Drivers (punctuation upgrades)

Hold up to 6. Each goes to level 5 (COLON.SYS: level 2). Bonuses are per level.

| Driver | Bonus |
|---|---|
| `!` EXCLAIM.SYS | +10% damage |
| `;` SEMICOL.SYS | -8% weapon delay |
| `:` COLON.SYS | +1 projectile / orbit / strike |
| `.` PERIOD.SYS | +10% move speed |
| `,` COMMA.SYS | +30% pickup range |
| `"` QUOTES.SYS | +10% area |
| `'` APOSTR.SYS | +15% duration, +10% projectile speed |
| `?` QUERY.SYS | +6% critical chance (x2 damage) |
| `~` TILDE.SYS | +0.3 HP per second |
| `^` CARET.SYS | +20 max HP |
| `` ` `` BACKTICK.SYS | +1 armor |
| `_` UNDERSC.SYS | +10% XP gain |

When everything is maxed out, level-ups offer **MEM.EXE** instead, which restores 40 HP.

![Pause screen with loadout and stats](images/pause.png)

### Pickups and treasure

| Symbol | What it is |
|---|---|
| `+` | XP. Cyan, green, yellow, then magenta as the value goes up |
| `♥` | Heart: restores 30 HP |
| `Ω` | Magnet: pulls all XP and bytes to you |
| `♦` | Bytes: your score |
| `[ZIP]` | Archive dropped by elites: pick 1 upgrade for something you own |
| `[≡]` | .TMP file: walk over it for random loot |
| `░▒░` | Deleted file: stand on it to UNDELETE buried treasure (an upgrade choice, a bytes and XP shower, two power-ups, or a full heal) |
| `→` | Yellow arrows at the screen edge point to nearby buried treasure |

### Power-ups

| Symbol | Power-up | Effect |
|---|---|---|
| `»»` | TURBO | 10s: weapons fire 60% faster, you move 25% faster |
| `^S` | CTRL+S | 5s: enemies freeze and can't hurt you |
| `☼` | SCANDISK | Kills every normal enemy on screen and hurts elites and the boss |
| `◘` | WRITE PROTECT | 6s: you take no damage |

![Gameplay with field pickups](images/gameplay2.png)

### Enemies and events

| Enemy | Name | First appears |
|---|---|---|
| `x` | bug | 0:00 |
| `0` | null ptr | 1:00 |
| `E` | error | 2:00 |
| `@` | worm | 3:00 |
| `#` | corrupt sector | 4:00 |
| `$` | memory leak | 5:00 |
| `&` | fork | 6:00 |
| `%` | overflow | 7:00 |
| `W` | boot virus | 8:00 |

- **Elites** appear at 0:45 and every minute after: big blinking enemies that drop a `[ZIP]`.
- **Fork bombs** at 2:30, 5:30 and 8:30: a ring of enemies closes in on you.
- **FATAL.EXE** loads at 10:00. Below half HP it adds a bullet spiral and spawns tougher minions.

![FATAL.EXE boss fight](images/boss.png)

### D:\ enemies and boss

| Enemy | Name | Notes |
|---|---|---|
| `q` | trojan | Fast, chases you hard |
| `k` | keylogger | Fires aimed shots every few seconds |
| `Z` | zip bomb | Tanky. Bursts into a ring of bullets when killed |

- **CHKDSK.EXE** loads at 10:00 on `D:\`. Fires radial bursts and aimed fans, and summons trojans. Below half HP it speeds up and adds a spiral.

Lose and you get `General failure reading drive C: Abort, Retry, Fail?`. Win and FATAL.EXE terminates normally.

![Win screen](images/complete.png)

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole game: code, graphics, sound (generated in the browser) and screens |
| `Web437_IBM_VGA_8x16.woff` | IBM VGA 8x16 font for the DOS look |
| `FONT-LICENSE.txt` | The font's license |
| `images/` | Screenshots for this README |

## Credits

Font: **Px437 / Web437 IBM VGA 8x16** from [The Ultimate Oldschool PC Font Pack](https://int10h.org/oldschool-pc-fonts/) by VileR, licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). See `FONT-LICENSE.txt`.
