# Weekend Warrior

An automatic flight assistant for DCS World. It flies the procedural parts of a sortie for you:
joining a tanker and taking fuel, getting home to a runway, and flying the carrier approach. Then it
hands the jet back to you. The **F/A-18C Hornet** and the **F-14B Tomcat** have every mode; the **F-16C**
has refuelling, RTB and the A/G trainer (it can't land on a carrier). See [Aircraft](#aircraft).

**[⬇ Download the latest version](https://github.com/erasma/dcs-weekend-warrior-releases/releases/latest)**
(get the `WeekendWarrior-….zip` file under *Assets*)

Weekend Warrior is free. If you'd like more aircraft supported, you can
**[buy me a coffee](https://buymeacoffee.com/erasma)** — it goes towards DCS modules to set up and test
(see [Support](#support)).

It talks to DCS only through DCS's own Export scripting. There is no kernel driver, no injected
input and no memory reading.

---

## What you need

- Windows 10 or 11, and DCS World with the **F/A-18C**, the **F-16C** and/or the **F-14B**. See [Aircraft](#aircraft)
  for which modes each one has.
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

**Updates are digitally signed.** From version 1.1.0 (build 450) on, the app only installs an update
that carries the Weekend Warrior release signature. If a download has been tampered with, or doesn't
come from us, the app refuses it and your current version stays exactly as it was. So update from
inside the app, or from this page, and never from a copy someone reposted elsewhere.

You can also press **Check for updates now** in Settings, or turn the startup check off there. You can
always update by hand: download the new zip and unzip it over the old folder.

---

## Aircraft

Each aircraft only gets the modes it has been set up for:

<!-- aircraft-table:start -->
| Aircraft | Refuel | RTB | Carrier | A/G |
|---|---|---|---|---|
| F-16C Viper | Yes (KC-135 boom) | Yes | Not capable | Yes |
| F/A-18C Hornet | Yes (drogue tankers) | Yes | Yes | Yes |
| F-14 Tomcat | Yes (drogue tankers) | Yes | Yes | Yes |
| Other aircraft | No | No | No | No |
<!-- aircraft-table:end -->

The Tomcat has been in the app since v1.2.0-b540: refuelling (the app works the probe and the speed brake; you make the two radio calls when it asks), RTB, Case 1 carrier landing and the A/G trainer (Jester sets up the pod and the weapon).

**[Full status per aircraft](aircraft/README.md)**: for every aircraft, what is live in the app you download and
how far the testing of each area (refuelling, A/G weapons, RTB, carrier) has got. It is updated as testing goes on.

A mode your aircraft isn't set up for is **greyed out** on the mode bar. Tapping it tells you
*"the … has not been set up for … yet"* and changes nothing. If you jump into a different aircraft,
the app moves to a mode that aircraft has.

---

## Support

Every aircraft has to be set up and flight-tested in its own DCS module before the app can fly it.
Donations go towards buying the modules I don't have yet:

**[☕ Buy me a coffee](https://buymeacoffee.com/erasma)**

Already set up: F/A-18C, F-16C and F-14B. Modules I already have, so these
are the next ones to be set up: A-10C II, AV-8B Harrier, AJS-37 Viggen and M-2000C.

---

## Using it

You drive everything by **clicking the overlay**, the small panel over the game (drag it wherever
you like):

- **Pick a mode** on the bar along the top: **REFUEL · RTB · CARRIER · A/G** (modes your aircraft
  doesn't have are greyed)
- **Click the buttons** under it. They change with the mode and with what the jet is doing, so the
  button you need next is always the one showing.
- **Pick from the list** (tanker, runway, deck or weapon) by clicking a row
- **⚙** opens Settings, and **▾** collapses the panel
- **EXIT** closes the app: click once (it turns red, `CONFIRM?`), then click again within 3 s

**END (the red button) always gives you the jet back.** So does switching mode or exiting the app.
Nothing is left holding your stick.

<details>
<summary>Optional: keyboard shortcuts</summary>

You don't need these, and they are **off unless you turn them on**: Settings → Controls →
*Keyboard shortcuts*. Once on, the main buttons also have keys: **Scroll Lock** = the main (blue)
button, **Num Lock** = NEXT, **End** = END, **Insert** = switch mode, **Home** = overlay text on/off.
You can move each one to another key in the same place.

When they are on, they work **anywhere in Windows**, not only in DCS. Pressing End in another
program still ends what the app is flying.

</details>

Spoken prompts tell you what the app is doing and what it wants from you next.

### REFUEL

**Hornet:** fly within a sensible distance of a drogue tanker (KC-135 MPRS, KC-130, S-3B, IL-78). The
plain KC-135 is a boom tanker and cannot refuel a Hornet; the app will tell you so.

**F-16C:** use a **boom** tanker (the plain KC-135). The drogue tankers can't refuel an F-16, and the
app greys them out. It opens the air-refuel door for pre-contact and closes it when you're full. The
buttons are the same as the Hornet's.

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

**F-16C:** **TARGET SEARCH** picks the enemy and **TARGET WAYPOINT** puts steerpoint 59 on it. **FLIR SETUP**
slaves the targeting pod to it and point-tracks it, and **WEAPON SETUP** readies the chosen weapon (laser bombs,
Mavericks, JDAM, JSOW, CBU-103/105, HARM, dumb and cluster bombs, rockets, gun). You fly, lase and release. In
multiplayer each jet uses its own steerpoint 59.

---

## Settings

Open with **⚙** on the overlay. The useful ones:

- **Controls**: turn the optional keyboard shortcuts on or off, and choose their keys.
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

- CARRIER is for the Hornet and the F-14 Tomcat (the F-16C can't land on a carrier). The F-16C has REFUEL, RTB and A/G.
- Hornet carrier on a long straight-in (for example from **GET TO CARRIER**): the last mile can be flown slightly high, so the jet floats past the wires and bolters. It climbs away safely and comes round for another pass. Short approaches trap reliably (v1.2.0-b556).
- Hornet RTB in a crosswind: it can hold 30-40 m off the centreline on final and touch down off centre.
- F-16C and F-14 RTB: in a crosswind the rollout can drift up to about 20 m off the centreline after touchdown (it stays on the runway).
- F-14 carrier landing has been flown at one weight only (about 52,600 lb). F-14 multiplayer is not tested yet.
- Jester occasionally does not respond at mission start. If WEAPON SETUP says Jester did not select the station, restart the mission.
- Case 2&3 hands over at ~6 nm. You couple the ACLS and make the radio calls.
- The A/G trainer is guided, not automatic: it sets the jet up, and you fly, lase and release. On the Hornet some
  weapons are not yet verified in the jet (marked **?**); every F-16C weapon in the list has been tested.
- Carrier trims start at zero on a deck the app has not landed on before.

---

## Contributors

- **erasma**: author and test pilot
- AI coding assistant, wrote parts of the code

---

## Versions

Each release is tagged `v<version>-b<build>`. See
[Releases](https://github.com/erasma/dcs-weekend-warrior-releases/releases) for what changed.
