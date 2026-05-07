# Vietnam Airlines — AR Luggage Measure Wireframes

Wireframes for the AR/VR luggage measuring feature in the Vietnam Airlines mobile app.

## Feature Overview

Passengers can measure their luggage (carry-on or checked bag) using their phone camera before arriving at the airport. Two measurement methods are available per luggage type, selectable via tabs on the scan screen.

---

## Luggage Types & Methods

| Luggage Type | Tab: LiDAR Scan | Tab: Auto Scan |
|---|---|---|
| **Carry-on** | LiDAR nodes auto-measure bag dimensions | AR box overlay on floor — passenger places bag inside to self-assess |
| **Checked Bag** | LiDAR nodes auto-measure bag dimensions | Scan floor, then drag to mark L × W × H manually |

**LiDAR Scan** requires iPhone 12 Pro or newer (devices with a LiDAR sensor).  
**Auto Scan** works on all devices.

---

## User Flow

```
Select Luggage Type (Carry-on / Checked Bag)
        ↓
AR Scan Screen
  ┌─────────────────────────┐
  │  [ LiDAR ] [ Auto Scan ]│  ← tabs at top
  │  ─────────────────────  │
  │       AR Camera View    │
  │    (content adapts to   │
  │      selected tab)      │
  │  ─────────────────────  │
  │  Instructions + CTA     │
  └─────────────────────────┘
        ↓
Result Screen (Pass / Fail + dimensions)
```

---

## Wireframe Files

| File | Description |
|---|---|
| [`wireframes-wiretext.md`](wireframes-wiretext.md) | All screens as editable Wiretext links |
| [`vi-flow-carry-on-box.txt`](vi-flow-carry-on-box.txt) | Vietnamese wireframe — carry-on box + LiDAR flows |

---

## Carry-on Size Limits
- **Max dimensions:** 56 × 36 × 23 cm
- **Max weight:** 10 kg

## Checked Bag Size Limits
- **Max linear total (L+W+H):** 158 cm
- **Max weight:** 23 kg

> Limits may vary by fare class and booking type.
