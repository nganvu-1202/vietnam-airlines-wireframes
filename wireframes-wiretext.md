# Wireframes — Wiretext Links

All screens are editable in [Wiretext](https://wiretext.app). Click any link to open the wireframe in the editor.

---

## 1. Entry Flow — Luggage Type & Method Selection (Updated: Tab Design)

**Screens:** Luggage type selector → Carry-on scan (LiDAR tab / Auto Scan tab) → Checked bag scan (LiDAR tab / Auto Scan tab)

> This is the **updated design** where method selection happens via tabs on the scan screen, not a separate screen.

[Open Wireframe →](https://wiretext.app/w/V2RQseEa)

**Screens included:**
- `S1` Luggage type selection (Carry-on / Checked Bag cards)
- `S2` Carry-on scan — LiDAR tab active
- `S3` Carry-on scan — Auto Scan tab active (AR box overlay)
- `S4` Checked bag scan — LiDAR tab active
- `S5` Checked bag scan — Auto Scan tab active (floor drag)

---

## 2. Carry-on — Box Overlay (Auto Scan) Method

**Screens:** Camera permission → Floor scan → AR box appears → Self-assessment → Pass → Fail

[Open Wireframe →](https://wiretext.app/w/ygki1-AL)

**Screens included:**
- Camera permission request
- AR floor scanning with progress bar
- AR box projection on floor (56×36×23 cm limit)
- Self-assessment prompt ("Does your bag fit?")
- Result: PASS — bag within carry-on limits
- Result: FAIL — bag exceeds limits, options to measure again or check bag in

---

## 3. Carry-on — LiDAR Scan Method

**Screens:** Point at bag → Walk around (nodes form) → Mesh complete → Auto result

[Open Wireframe →](https://wiretext.app/w/4iPgiqdD)

**Screens included:**
- Point camera at bag — initial LiDAR nodes appear at edges
- Walk around bag — nodes connect (progress: 65%)
- Mesh complete — analyzing dimensions
- Auto result with measured dimensions (accuracy: ±1 cm)

---

## 4. Checked Bag — Manual Measure (Auto Scan) Method

**Screens:** Floor scan → Drag to mark length → Drag to mark width → Tilt drag for height → Result

[Open Wireframe →](https://wiretext.app/w/iV9zEHb5)

**Screens included:**
- AR floor scanning
- Step 2: Drag horizontally to mark bag length
- Step 3: Drag perpendicular to mark bag width
- Step 4: Tilt phone sideways, drag vertically for height
- Result: total linear measurement vs 158 cm limit

---

## 5. Edge States + Checked Bag LiDAR Fail Result

**Screens:** LiDAR not supported → Camera permission denied → Scan failed → Checked bag LiDAR fail

[Open Wireframe →](https://wiretext.app/w/2eZNvFBG)

**Screens included:**
- LiDAR not supported — device fallback to manual method
- Camera access denied — Settings redirect flow
- Scan incomplete — tips for retry (lighting, movement, distance)
- Checked bag LiDAR result: FAIL — dimensions exceed 158 cm linear limit

---

## Notes

- **Checked bag LiDAR (pass result)** reuses the same screens as Wireframe 3 (Carry-on LiDAR), with different size limits applied at the result screen.
- **LiDAR** requires iPhone 12 Pro / iPad Pro 2020 or newer.
- **Auto Scan fallback** works on all devices — no special hardware needed.
- Height measurement in the manual method requires the user to tilt the phone sideways — this step is the most friction-heavy and worth prototype testing.
