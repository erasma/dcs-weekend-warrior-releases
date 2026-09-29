# Weekend Warrior

An automatic flight assistant for the **F/A-18C Hornet** in DCS World. It flies the procedural parts
of a sortie for you: joining a tanker and taking fuel, getting home to a runway, and flying the
carrier approach. Then it hands the jet back to you.

**[⬇ Download the latest version](https://github.com/erasma/dcs-weekend-warrior-releases/releases/latest)**
(get the `WeekendWarrior-….zip` file under *Assets*)

It talks to DCS only through DCS's own Export scripting. There is no kernel driver, no injected
input and no memory reading.

---

## What you need

- Windows 10 or 11, and DCS World with the **F/A-18C**. No other aircraft is supported.
- Single-player, or a multiplayer server you host yourself.
- DCS set to **borderless or windowed** mode if you want the on-screen overlay. In exclusive
  full-screen, or in VR, use the in-game text option instead (see [Settings](#settings)).

Nothing else. Python and every library the app needs are inside the download.

---

## Install (about 2 minutes)

1. **Download** `WeekendWarrior-<version>.zip` from the
   [latest release](https://github.com/erasma/dcs-weekend-warrior-releases/releases/latest).
2. **Unzip it** to a folder you own, for example your Desktop or `Documents\WeekendWarrior`.
   Don't use `Program Files`: the app keeps its settings in its own folder and updates itself there.
3. **Run `WeekendWarrior.exe`.**
   Windows may say *"Windows protected your PC"*, because the app is not code-signed. Click
   **More info → Run anyway**. You only have to do this once.
4. **Install the DCS hook (once).** The app starts as a small overlay at the top-left of the screen.
   Click **⚙** on it to open Settings, then press **Install hook into DCS**.
   This writes `WeekendWarrior.lua` into `Saved Games\DCS\Scripts\`, and it adds one loader line to
   `Export.lua` (creating that file if you have none), plus a small in-game text hook in
   `Scripts\Hooks\`. Your existing export scripts, such as SRS or Tacview, are left alone, and
   nothing in the DCS install folder is changed.
   If it says *"No DCS profile found"*, start DCS once so it creates `Saved Games\DCS`, then try again.
5. **Restart DCS** once so it loads the hook.

That's it. Start the app before or after DCS, whichever you like. It picks up the jet once you are in
the cockpit.

To **uninstall**, delete the folder. To remove the hook as well, delete
`Saved Games\DCS\Scripts\WeekendWarrior.lua` and `Saved Games\DCS\Scripts\Hooks\WW-Overlay.lua`,
and remove the line ending in `-- WeekendWarrior` from `Scripts\Export.lua`.

---

## Updates

When the app starts, it checks this page for a newer version. If there is one, it asks:

> **Install and restart** · **Later** · **Skip this version**

**Install** downloads the new version, checks it isn't corrupt, swaps it in and restarts the app.
Your settings, carrier trims and flight models are kept. It never asks while it is flying the jet
for you.

You can also press **Check for updates now** in Settings, or turn the startup check off there. You can
always update by hand: download the new zip and unzip it over the old folder.

---

## Using it

Everything is on the **overlay**, the small panel over the game (drag it wherever you like):

- The **mode bar** along the top: **REFUEL · RTB · CARRIER · A/G**
- The **buttons** under it change with the mode and with what the jet is doing
- **⚙** opens Settings, **▾** collapses the panel
- **EXIT** closes the app: tap once (it turns red, `CONFIRM?`), tap again within 3 s

You can also use the keyboard. You can change these keys in Settings:

| Key | Does |
|---|---|
| **Scroll Lock** | START / the main action (START APPROACH, TAKE THE JET, …) |
| **Num Lock** | NEXT (next tanker, next field, next deck) |
| **End** | END: stop and give the jet back to you immediately |
| **Insert** | Switch mode |
| **Home** | Overlay text on/off |

**END always gives you the jet back.** So does switching mode or exiting the app. Nothing is left
holding your stick.

Spoken prompts tell you what the app is doing and what it wants from you next.

### REFUEL

Fly within a sensible distance of a drogue tanker (KC-135 MPRS, KC-130, S-3B, IL-78). The plain
KC-135 is a boom tanker and cannot refuel a Hornet; the app will tell you so.

- **START**: joins the tanker, holds 1 nm back, then **MOVE TO PRE-CONTACT** and **MOVE IN TO
  CONTACT** take it in to the basket, and it takes fuel. When you are full it breaks away and offers
  **TAKE THE JET**.
- **TANKER FORMATION**: flies out and holds formation on the tanker, without refuelling.
- **NEXT TANKER**: picks another tanker when there are several. **BREAKAWAY (1 NM)** backs off at
  any point.
- Make the radio calls to the tanker yourself.

### RTB (runway landing)

- Pick a field (**NEXT FIELD** cycles through them), then **START APPROACH**. It flies the circuit,
  final and flare, and brakes to a full stop.
- **GET TO RTB**: flies you out to the approach first, then hands over on profile.
- **TAKE THE JET** (when offered) or **END** gives you control.

### CARRIER

- Pick the ship (**NEXT DECK**), then choose:
  - **CASE 1 - LADDER**: flies the visual pattern and the ball, all the way to the deck.
  - **CASE 2&3 - ACLS**: sets up TACAN, ICLS, Link 4 and the course line, flies the ship's own
    commanded approach, and **hands the jet to you at about 6 nm**. From then on it touches nothing.
    **You** press ATC and CPL to couple. The app will not do it for you. Keep the stick centred
    while you couple.
- **GET TO CARRIER**: flies you to the approach first.
- A new carrier starts with no trim, so the first few traps on a deck it hasn't landed on may be
  off. Use **Settings → Carrier trims** to nudge the aim point for that deck.

### A/G (air-to-ground trainer)

A guided trainer for the targeting pod and weapons. **FLIR SETUP** gets the pod ready and on a
target, and **WEAPON SETUP** sets the chosen weapon ready to release. **TARGET SEARCH**,
**PREV** and **NEXT** pick targets, **WEAPON** picks the weapon, and **TARGETS** widens the search
cone. It sets up the switches and talks you through them. **You fly the attack and release.**
Weapons marked **?** / *NOT VERIFIED in the jet* are best-effort. If a step can't be done for you,
the app tells you which button to press.

---

## Settings

Open with **⚙** on the overlay. The useful ones:

- **Controls**: rebind every key above.
- **Transparent overlay panel**: the on-screen panel (needs borderless/windowed DCS).
- **Also show prompts as DCS mission text**: shows the prompts inside the game, for **VR** or
  full-screen.
- **Spoken prompts**, with a volume slider.
- **Check for updates when the app starts**, **Check for updates now**, **Install hook into DCS**.
- **Carrier trims**: per carrier, in 0.5 m steps.

---

## Troubleshooting

| Problem | Try |
|---|---|
| The app never reacts to the jet | The hook isn't loaded. Press **Install hook into DCS** in Settings, then **restart DCS**. |
| Overlay not visible over the game | Set DCS to borderless or windowed, or turn on *show prompts as DCS mission text*. |
| "Windows protected your PC" | **More info → Run anyway** (the app is not code-signed). |
| Update fails | Check you unzipped to a folder you can write to (not Program Files). `ww-update.log` in the app folder says what happened. If it goes wrong, download the zip and unzip it over the folder. |
| Something odd happened | Send `ww-app.log` from the app folder along with a description. |

---

## Known limitations

- F/A-18C only.
- Case 2&3 hands over at ~6 nm. You couple the ACLS and make the radio calls.
- The A/G trainer is guided, not automatic, and some weapons are not verified in the jet.
- Carrier trims start at zero on a deck the app has not landed on before.

---

## Versions

Each release is tagged `v<version>-b<build>`. See
[Releases](https://github.com/erasma/dcs-weekend-warrior-releases/releases) for what changed.
