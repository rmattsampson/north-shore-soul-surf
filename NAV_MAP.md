# North Shore -- Soul Surf: World Map

Two rows of screens, west (left) to east (right). Each beach has a land screen directly below it.

```
            WEST  <------------------------------------------------------------------------>  EAST
 BEACH ROW   HALEIWA  <->  TOWN  <->  SURF  <->  COVE  <->  WAIMEA  <->  PIPELINE  <->  SUNSET
  (y: sand)     |           |          |          |           |             |              |
  walk DOWN     v           v          v          v           v             v              v
 LAND ROW    KAM HWY  <->  MY PLACE <-> RCVA   <-> SHAPING <-> CANE    <->  HUI       <->  LOOKOUT
                           (cabin)     HOUSE      BARN       FIELDS        CLUBHOUSE      TRAIL
                                       + Auntie's (COVEDOWN)
```

| Screen (SCR id) | Row | Left | Right | Up | Down | Doors / water |
|---|---|---|---|---|---|---|
| HALEIWA (6) | beach | wall | TOWN | paddle out (any rank) | KAM HWY | river mouth + footbridge |
| TOWN (0) | beach | HALEIWA | SURF | paddle out | MY PLACE | |
| SURF (1) | beach | TOWN | COVE | paddle out | RCVA HOUSE | Chandler's hale |
| COVE (2) | beach | SURF | WAIMEA | paddle out | SHAPING BARN | photographer (coins) |
| WAIMEA (7) | beach | COVE | PIPELINE | paddle out (Charger) | CANE FIELDS | |
| PIPE (8) | beach | WAIMEA | SUNSET | paddle out (final: all levels) | HUI CLUBHOUSE | Pipe Masters judge |
| SUNSET (9) | beach | PIPELINE | wall | paddle out (Local) | LOOKOUT | |
| KAMHWY (10) | land | wall | MY PLACE | HALEIWA | -- | SURF SHOP (B: boards, trunks, shirts), SHAVE ICE stand (B: treats for Andy), shrimp truck + line, bus |
| MYHOUSE (4) | land | KAM HWY | RCVA HOUSE | TOWN | -- | MY PLACE door |
| HOUSE (3) | land | MY PLACE | SHAPING BARN | SURF | -- | RCVA door, Auntie's (across trail), Billabong yard |
| COVEDOWN (5) | land | RCVA HOUSE | CANE | COVE | -- | Shaping Barn door |
| CANE (11) | land | SHAPING BARN | HUI | WAIMEA | -- | pickup w/ foam blanks |
| HUIHALE (12) | land | CANE | LOOKOUT | PIPELINE | -- | Hui door (Charger) |
| LOOKOUT (13) | land | HUI | wall | SUNSET | -- | |
| SKATE (14) | 3rd row, under KAM HWY | wall | wall | KAM HWY (gate) | -- | loaner skateboard (B), pool. The board can't leave the park. |

KAM HWY's down exit leads to the SKATE park, which sits in the bottom-left corner of the map. Sterling's Billabong yard (HOUSE) is a no-landing zone: you can walk in through its gate, but a screen change never drops you inside it.

## Transition rules (code: `goScreen()` in index.html)
- **Left/right edge:** come out on the opposite edge of the neighbor at the **same y** (left edge x=14, right edge x=W-14).
- **Down off a beach:** come out at the **top** of the land screen below (y=SEATOP+18) at the **same x**.
- **Up off a land screen:** come out at the **bottom** of the beach above (y=H-22) at the **same x**.
- If a solid thing (house, truck, fence, river) is on the arrival spot, `goScreen` moves you to the nearest free spot.
- **Doors:** leaving a room always puts you outside that room's front door (`ROOMS[id].sx/sy`).
- **Water:** paddling in keeps your x and drops you at the waterline. The water view has no side exits.
- Don't use the old per-screen position memory (`restorePos`) for edges. It caused the "popping into the wrong place" bug.
