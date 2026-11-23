# bmw-idrive-claude

Root your own BMW iDrive 7 / 8 head unit with Claude as the co-pilot, then install apps BMW never shipped: an app store on the dash, Waze on the cluster and HUD, YouTube, a browser, live engine data, fault codes, even Doom.

You bring 1 ENET cable and 1 laptop. Claude reads the tool READMEs, checks the car read-only first, and refuses to flash until your coding backup exists.

> Head unit only. This does not touch engine, brakes or airbags.
> Video apps are for passengers only. Watching video while driving is illegal in most places.

## What you need

- ENET (Ethernet to OBD) cable
- A laptop (Windows, macOS or Linux, Python 3.9+)
- A battery charger or stable power. The car stays parked during flashing and installs.
- A coding backup tool: BimmerCode, or ISTA / E-Sys
- Claude Code (or any Claude agent that can run shell commands)

## The 5 steps

| Step | What happens | Can it be undone? |
|---|---|---|
| 1 | ENET cable into the OBD port, laptop on the other end | yes |
| 2 | Claude reads the root tool's README and runs a read-only status check | yes, nothing is written |
| 3 | Back up your coding (CAFD). The flash can wipe it, and your Digital Key pairings | this backup IS your undo |
| 4 | One flash command. Claude confirms `uid=0(root)` and runs `persist` | only with the backup |
| 5 | Install the MGU Store and pick apps like on a phone | yes |

## Start

1. Copy [`CLAUDE.md`](CLAUDE.md) into an empty folder and open Claude Code there.
2. Paste this:

```
I want to root the iDrive head unit in my own BMW and install the MGU Store.
Follow CLAUDE.md exactly. Start with step 1 and stop at every gate.
```

Claude asks for your car model and iDrive version, reads the READMEs below, and walks you through the steps. It will not run any write command until the backup gate in step 3 passes.

## The stack (all credit to the authors)

| What | Repo |
|---|---|
| Root over ENET (SSH, `uid=0`) | [cauliflowermossgrape/idrive7-8-ssh-root](https://github.com/cauliflowermossgrape/idrive7-8-ssh-root) |
| App store for the head unit | [robertnisipeanu/mgu-store](https://github.com/robertnisipeanu/mgu-store) |
| Waze on cluster + HUD | [robertnisipeanu/idrive-apps](https://github.com/robertnisipeanu/idrive-apps) |
| YouTube | [JustAnotherPU/ridetube](https://github.com/JustAnotherPU/ridetube) |
| 50+ more apps and docs | [FidelisClayton/awesome-bmw-mgu](https://github.com/FidelisClayton/awesome-bmw-mgu) |

This repo only adds the Claude workflow and safety gates on top. Read each project's own README and license before you run anything.

## Known limits

- The MGU Store says iDrive 8 is tested only in an emulator so far.
- The browser app is experimental.
- Rooting can wipe coding and Digital Key pairings. Back up first.
- Dealers may reflash or treat it as a warranty issue.

## Credits

- Root and app tools: the authors linked above.
- Demo footage in the launch post: @0xCodez and BMW life 2.0 on YouTube.
- Workflow and gates: [f0rgent](https://f0rgent.github.io)

---

Don't have Claude Code yet? [Get Claude here](https://claude.ai/referral/IL0FPScZCw).
