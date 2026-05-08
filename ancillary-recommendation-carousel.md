# Gợi ý Dịch vụ Phụ trợ — Carousel Trang Chủ

[Chỉnh sửa trong Wiretext](https://wiretext.app/w/UEEFQLTW)

## Tổng quan

Wireframe mô tả carousel gợi ý dịch vụ phụ trợ trên trang chủ app Vietnam Airlines. Engine đề xuất dựa trên rule-based scoring:

```
priority_score = base_score + route_bonus + passenger_count_bonus
               + time_to_departure_bonus + tier_bonus
               − already_purchased_penalty
```

## 3 Kịch bản (KB)

### KB1: Nội địa, Solo, T-7
- **Chuyến bay:** SGN → HAN, 1 hành khách, Economy, còn 7 ngày
- **Top 3 đề xuất:**
  1. Hành lý ký gửi (score=92) — badge "Phổ biến nhất"
  2. Pre-order F&B (score=78)
  3. Chọn chỗ ngồi (score=71)
- **Carousel:** 5 dots (5 dịch vụ khả dụng)

### KB2: Quốc tế, 4 HK, T-1 (Khẩn cấp)
- **Chuyến bay:** SGN → NRT, 4 hành khách, Economy, bay ngày mai
- **Đặc biệt:** Alert cảnh báo "Bay ngày mai!" (T-1 urgency bonus +25)
- **Top 3 đề xuất:**
  1. Phòng chờ Lotus Lounge (score=95) — quốc tế + nhóm
  2. Hành lý ký gửi (score=88) — giá tổng cho 4 HK
  3. Ưu tiên làm thủ tục (score=82)
- **Carousel:** 4 dots (F&B ẩn vì điểm thấp cho quốc tế nhóm)

### KB3: Business Class, Solo
- **Chuyến bay:** HAN → ICN, 1 hành khách, Business, còn 12 ngày
- **Đặc biệt:** Lounge và Priority Check-in đã bao gồm trong hạng vé → ẩn khỏi carousel (already_purchased_penalty = -100)
- **Top 3 đề xuất:**
  1. Hành lý thêm 10kg (score=68) — Business đã có 30kg
  2. F&B Premium Menu (score=62) — đặt trước miễn phí
  3. Bảo hiểm du lịch (score=45) — fallback item từ pool
- **Carousel:** 3 dots (2 DV đã ẩn + 1 fallback)

## Quy tắc Engine

| Yếu tố | Mô tả | Ví dụ |
|---------|--------|-------|
| base_score | Điểm cơ bản mỗi dịch vụ | Hành lý=50, Lounge=45 |
| route_bonus | Nội địa vs quốc tế | Nội địa: Hành lý +20; Quốc tế: Lounge +20 |
| passenger_count_bonus | Số HK > 1 | 4 HK: +15 cho Lounge, Hành lý |
| time_to_departure_bonus | Gần ngày bay | T-1: +25 (max), T-7: +15 |
| tier_bonus | Hạng vé | Business: +10 cho F&B Premium |
| already_purchased_penalty | Đã mua/bao gồm | Business Lounge: -100 → ẩn |

## Wireframe ASCII

```
 ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓     ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓     ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
 ┃                              ┃     ┃                              ┃     ┃                              ┃
 ┃  9:41    VN Airlines  ≡      ┃     ┃  9:41    VN Airlines  ≡      ┃     ┃  9:41    VN Airlines  ≡      ┃
 ┃                              ┃     ┃                              ┃     ┃                              ┃
 ┃  ┌────────────────────────┐  ┃     ┃  ┌────────────────────────┐  ┃     ┃  ┌────────────────────────┐  ┃
 ┃  │ SGN → HAN              │  ┃     ┃  │ SGN → NRT              │  ┃     ┃  │ HAN → ICN              │  ┃
 ┃  │                        │  ┃     ┃  │                        │  ┃     ┃  │                        │  ┃
 ┃  ├────────────────────────┤  ┃     ┃  ├────────────────────────┤  ┃     ┃  ├────────────────────────┤  ┃
 ┃  │ 15 Thg 5 | 1 HK        │  ┃     ┃  │ 14 Thg 5 | 4 HK        │  ┃     ┃  │ 20 Thg 5 | 1 HK        │  ┃
 ┃  │ Nội địa · Economy      │  ┃     ┃  │ Quốc tế · Economy      │  ┃     ┃  │ Quốc tế · Business     │  ┃
 ┃  └────────────────────────┘  ┃     ┃  └────────────────────────┘  ┃     ┃  └────────────────────────┘  ┃
 ┃                              ┃     ┃                              ┃     ┃                              ┃
 ┃  Đề xuất cho bạn             ┃     ┃  ┌────────────────────────┐  ┃     ┃  Đề xuất cho bạn             ┃
 ┃  Dựa trên chuyến bay         ┃     ┃  │ ! Bay ngày mai!        │  ┃     ┃  (Ẩn: Lounge, Priority)      ┃
 ┃                              ┃     ┃  └────────────────────────┘  ┃     ┃                              ┃
 ┃  ┌────────────────────────┐  ┃     ┃  Đề xuất cho bạn             ┃     ┃  ┌────────────────────────┐  ┃
 ┃  │ ★ Hành lý ký gửi       │  ┃     ┃  ┌────────────────────────┐  ┃     ┃  │ Hành lý thêm 10kg      │  ┃
 ┃  │                        │  ┃     ┃  │ Phòng chờ Lotus        │  ┃     ┃  │                        │  ┃
 ┃  ├────────────────────────┤  ┃     ┃  │                        │  ┃     ┃  ├────────────────────────┤  ┃
 ┃  │ 20kg từ 180.000đ       │  ┃     ┃  ├────────────────────────┤  ┃     ┃  │ +10kg bổ sung          │  ┃
 ┃  │ ★ Phổ biến nhất        │  ┃ ───→┃  │ SGN Intl Terminal      │  ┃ ───→┃  │ từ 250.000đ            │  ┃
 ┃  └────────────────────────┘  ┃     ┃  │ từ 450.000đ/người      │  ┃     ┃  └────────────────────────┘  ┃
 ┃  ┌────────────────────────┐  ┃     ┃  └────────────────────────┘  ┃     ┃  ┌────────────────────────┐  ┃
 ┃  │ Pre-order F&B          │  ┃     ┃  ┌────────────────────────┐  ┃     ┃  │ F&B Premium Menu       │  ┃
 ┃  │                        │  ┃     ┃  │ Hành lý ký gửi         │  ┃     ┃  │                        │  ┃
 ┃  ├────────────────────────┤  ┃     ┃  │                        │  ┃     ┃  ├────────────────────────┤  ┃
 ┃  │ Đặt trước bữa ăn       │  ┃     ┃  ├────────────────────────┤  ┃     ┃  │ Menu Business class    │  ┃
 ┃  │ từ 99.000đ             │  ┃     ┃  │ 4 HK x 23kg/người      │  ┃     ┃  │ Đặt trước miễn phí     │  ┃
 ┃  └────────────────────────┘  ┃     ┃  │ từ 720.000đ tổng       │  ┃     ┃  └────────────────────────┘  ┃
 ┃  ╭────────────────────────╮  ┃     ┃  └────────────────────────┘  ┃     ┃  ┌────────────────────────┐  ┃
 ┃  │                        │  ┃     ┃  ╭────────────────────────╮  ┃     ┃  │ Bảo hiểm du lịch       │  ┃
 ┃  │    Chọn chỗ ngồi...    │  ┃     ┃  │                        │  ┃     ┃  │                        │  ┃
 ┃  ╰────────────────────────╯  ┃     ┃  │   Ưu tiên thủ tục...   │  ┃     ┃  ├────────────────────────┤  ┃
 ┃                              ┃     ┃  ╰────────────────────────╯  ┃     ┃  │ AIG [fallback]         │  ┃
 ┃         ● ○ ○ ○ ○            ┃     ┃                              ┃     ┃  └────────────────────────┘  ┃
 ┃                              ┃     ┃           ● ○ ○ ○            ┃     ┃                              ┃
 ┃  ┌────────────────────────┐  ┃     ┃  ┌────────────────────────┐  ┃     ┃           ● ○ ○              ┃
 ┃  │ Hm │ Bk │ Tr │ Me      │  ┃     ┃  │ Hm │ Bk │ Tr │ Me      │  ┃     ┃  ┌────────────────────────┐  ┃
 ┃  └────────────────────────┘  ┃     ┃  └────────────────────────┘  ┃     ┃  │ Hm │ Bk │ Tr │ Me      │  ┃
 ┃                              ┃     ┃                              ┃     ┃  └────────────────────────┘  ┃
 ┃                              ┃     ┃                              ┃     ┃                              ┃
 ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛     ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛     ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛
  KB1: Nội địa, Solo, T-7          KB2: Quốc tế, 4 HK, T-1            KB3: Business, Solo
  Score: Hành lý=92, F&B=78        ⚠ T-1 urgency bonus +25            Business filter active
  Ghế=71, Priority=45              Lounge=95, Hành lý=88              Ẩn DV đã bao gồm hạng vé
```
