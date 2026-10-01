# F/A-18C Hornet

Status on 2026-10-01. Player app version: **v1.1.0 (build 466)**.

**Live** = in the player app you download. **Testing** = where this area stands against the test
standard below. An area is only added to the player app once it has fully passed its test.

| Area | Player app | Testing |
|---|---|---|
| Air-to-air refuelling | 🟢 Live (since v1.0) | ✅ Passed the standard |
| A/G weapons | 🟢 Live (since v1.0) | 🟡 In testing |
| RTB (runway landing) | 🟢 Live (since v1.0) | ✅ Passed the standard |
| Carrier landing | 🟢 Live (since v1.0) | ✅ Passed the standard |

- **Air-to-air refuelling:** Drogue tankers. Passed: signed off by the developer on 2026-10-01.
- **A/G weapons:** Systems mode. 20 weapons and the Litening pod confirmed with a DCS hit/fire record on TESTING builds (Sept 2026). Walleye (AGM-62) and SLAM-ER blocked. The full DCS munition list for the Hornet is still to be built and run to the new standard.
- **RTB (runway landing):** Passed: signed off by the developer on 2026-10-01. On record: hands-free full stops at 1,000 kg and 2,900 kg fuel (build 191).
- **Carrier landing:** Passed: signed off by the developer on 2026-10-01. Hands-free approach with ACLS coupling; traps on record from builds 165, 169 and 187.

## A/G weapons: 20 of 22 passed

Weapon rows from SYSTEMS-WEAPONS-STATUS.md (TESTING builds, Sept 2026).

### Guided (must lock and hit)

| Weapon | Type | Result | Evidence |
|---|---|---|---|
| GBU-12 | Laser bomb | ✅ Passed | Kill, DCS hit record. |
| GBU-10 / GBU-16 | Laser bomb | ✅ Passed | Both destroyed their targets. |
| GBU-24 | Laser bomb | ✅ Passed | Kill on the SAM target. |
| GBU-31 JDAM | GPS bomb | ✅ Passed | Kill. |
| GBU-32 JDAM | GPS bomb | ✅ Passed | Kill (multiplayer server). |
| GBU-38 JDAM | GPS bomb | ✅ Passed | Kill. |
| AGM-154A JSOW | GPS glide weapon | ✅ Passed | Hit. |
| AGM-154C JSOW | GPS glide weapon | ✅ Passed | Hit. |
| AGM-65E Maverick | Missile (laser) | ✅ Passed | Kill; to re-check with a hit record. |
| AGM-65F Maverick | Missile (IR) | ✅ Passed | Kill. |
| AGM-88C HARM | Anti-radiation | ✅ Passed | Hit on the SAM radar. |
| AGM-84D Harpoon | Anti-ship | ✅ Passed | Ship destroyed. |
| AGM-62 Walleye | TV bomb | 🔴 Failed / blocked | Blocked: the seeker locks whatever is under the crosshair. |
| AGM-84H SLAM-ER | Datalink missile | 🔴 Failed / blocked | Blocked: needs a datalink step and a fuze preset. |

### Unguided (must fire)

| Weapon | Type | Result | Evidence |
|---|---|---|---|
| Mk-82 | Bomb | ✅ Passed | Fired. |
| Mk-83 | Bomb | ✅ Passed | Fired. |
| Mk-84 | Bomb | ✅ Passed | Fired. |
| Mk-20 Rockeye | Cluster | ✅ Passed | Fired. |
| CBU-99 | Cluster | ✅ Passed | Fired. |
| Zuni | Rockets | ✅ Passed | Fired. |
| Hydra | Rockets | ✅ Passed | Fired. |
| M61 gun | Gun | ✅ Passed | Fired. |


## The test standard

- **Air-to-air refuelling:** Automatic flight with real radio calls: join the tanker, connect, fill. Pass = fuel to full and a clean disconnect, no crash, no tanker collision.
- **A/G weapons:** Every air-to-ground munition the aircraft can carry, once each. Guided weapons must lock and HIT (laser within 30 m having steered, missiles / GPS / anti-radar within 10 m, or the target destroyed). Unguided weapons (bombs, cluster, rockets, gun) must be set up and FIRE.
- **RTB (runway landing):** Hands-free RTB to a runway at light, medium and heavy weight. Pass = touchdown in the touchdown zone on the centreline, gear intact, full stop on the runway, at all three weights.
- **Carrier landing:** Hands-free carrier approach. Pass = 3 traps in a row: a wire caught each time, no bolter, ramp strike or crash.

[All aircraft](README.md)
