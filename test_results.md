# TravelBuddy — Test Results

---

## Test 1 — Direct Answer (Không cần tool)

**Input:**
> Xin chào! Tôi đang muốn đi du lịch nhưng chưa biết đi đâu.

**Tool calls:** Không gọi tool

**Output:**
> Chào bạn! Rất vui được đồng hành cùng bạn lên kế hoạch cho chuyến đi sắp tới 🌴✨
>
> Để mình gợi ý điểm đến phù hợp nhất với nhu cầu và ví tiền của bạn, bạn chia sẻ thêm giúp mình 4 thông tin nhỏ này nhé:
> - 📍 **Bạn có định hướng địa điểm nào chưa?** Hoặc thích loại hình nào hơn: biển đảo, núi rừng, phố cổ, nghỉ dưỡng chill, hay săn ảnh/ẩm thực?
> - 📅 **Thời gian dự định đi?** (tháng nào, đi bao nhiêu ngày/đêm)
> - 👥 **Số người đi?** (1 mình, gia đình, hay nhóm bạn)
> - 💰 **Ngân sách dự kiến cho toàn bộ chuyến đi?** (khoảng bao nhiêu VNĐ)
>
> Cứ trả lời thoải mái, mình sẽ dựa trên đó tìm vé bay/khách sạn hợp lý và lên phương án chi tiết, tối ưu chi phí nhưng vẫn đảm bảo trải nghiệm "đã" nhất cho bạn nhé! 🎒✈️

**Kết quả:** ✅ PASS — Không gọi tool, hỏi lại đúng 4 thông tin cần thiết.

---

## Test 2 — Single Tool Call

**Input:**
> Tìm giúp tôi chuyến bay từ Hà Nội đi Đà Nẵng

**Tool calls:** `search_flights({'origin': 'Hà Nội', 'destination': 'Đà Nẵng'})`

**Output:**
> Dưới đây là một vài lựa chọn chuyến bay từ Hà Nội đi Đà Nẵng để bạn tham khảo nhé:
>
> ✈️ **VietJet Air** | 08:30 – 09:50 | Phổ thông | ~890.000đ *(giá tốt nhất)*
> ✈️ **Bamboo Airways** | 11:00 – 12:20 | Phổ thông | ~1.200.000đ
> ✈️ **Vietnam Airlines** | 06:00 – 07:20 | Phổ thông | ~1.450.000đ
> ✈️ **Vietnam Airlines** | 14:00 – 15:20 | Thương gia | ~2.800.000đ
>
> 💡 *Lưu ý:* Giá vé trên là mức ước tính, có thể dao động tùy theo thời điểm bạn đặt và số lượng ghế còn trống.
>
> Bạn dự định đi vào ngày nào, bao nhiêu người và muốn lưu trú mấy đêm? Nếu cần, mình có thể tìm khách sạn phù hợp với ngân sách và tính toán chi tiết tổng chi phí cho chuyến đi luôn nhé! 😊

**Kết quả:** ✅ PASS — Gọi đúng 1 tool, liệt kê đủ 4 chuyến bay, không bịa thêm.

---

## Test 3 — Multi-Step Tool Chaining

**Input:**
> Tôi ở Hà Nội, muốn đi Phú Quốc 2 đêm, budget 5 triệu. Tư vấn giúp!

**Tool calls:**
1. `search_flights({'origin': 'Hà Nội', 'destination': 'Phú Quốc'})`
2. `search_hotels({'city': 'Phú Quốc', 'max_price_per_night': 1500000})`
3. `calculate_budget({'total_budget': 5000000, 'expenses': 've_may_bay:2200000,khach_san:1600000'})`

**Output:**
> ✈️ Chuyến bay: VietJet Air chiều 16:00 - 18:15 (khứ hồi ước tính khoảng 2.200.000đ/người). Giờ này khá đẹp, đến nơi vừa kịp ngắm hoàng hôn trên biển.
>
> 🏨 Khách sạn: Lahana Resort 3⭐ tại Dương Đông (800.000đ/đêm). Với 2 đêm sẽ khoảng 1.600.000đ. Khách sạn rating 4.0, vị trí thuận tiện đi lại và ăn uống, phù hợp nhất trong tầm giá.
>
> 💰 Tổng chi phí ước tính: 3.800.000đ (đã gồm vé máy bay khứ hồi và 2 đêm khách sạn). Ngân sách còn lại: **1.200.000đ** để bạn dành cho ăn uống, di chuyển và vui chơi nhẹ nhàng nhé.
>
> 💡 Gợi ý thêm: Số tiền còn lại bạn có thể thuê xe máy (khoảng 120k-150k/ngày) để tự explore island, ghé chợ đêm Dương Đông ăn hải sản bình dân, hoặc tắm biển free ở Bãi Sao/Bãi Kem.

**Kết quả:** ✅ PASS — Gọi đúng 3 tool theo thứ tự, format expenses đúng, có bảng chi phí từ calculate_budget.

---

## Test 4 — Missing Info / Clarification

**Input:**
> Tôi muốn đặt khách sạn

**Tool calls:** Không gọi tool

**Output:**
> Chào bạn! Để mình tìm khách sạn ưng ý và đúng túi tiền cho bạn, bạn cho mình biết thêm 3 thông tin nhỏ nhé:
>
> 📍 **Thành phố/điểm đến** bạn muốn ở là đâu?
> 💸 **Ngân sách** bạn dự chi cho khách sạn khoảng bao nhiêu mỗi đêm?
> 📅 **Số đêm** bạn lưu trú (và ngày nhận/trả phòng nếu có)?
>
> Có đủ thông tin này mình check ngay giá và gợi ý chỗ nghỉ tốt nhất cho bạn nha! 😊

**Kết quả:** ✅ PASS — Không gọi tool, hỏi lại đúng các thông tin còn thiếu.

---

## Test 5 — Guardrail / Refusal (Off-topic)

**Input:**
> Giải giúp tôi bài tập lập trình Python về linked list

**Tool calls:** Không gọi tool

**Output:**
> Chào bạn! Mình là trợ lý du lịch của TravelBuddy, chuyên hỗ trợ lên kế hoạch du lịch, tìm vé máy bay, khách sạn và tính toán ngân sách cho các chuyến đi tại Việt Nam. Về bài tập lập trình Python hay các vấn đề code khác, mình không thể hỗ trợ trực tiếp được.
>
> Nếu bạn đang muốn lên một chuyến đi ngắn ngày để thư giãn sau giờ học, hay cần tư vấn vé máy bay, khách sạn phù hợp với ngân sách sinh viên/đi nhóm, cứ nhắn mình nhé!

**Kết quả:** ✅ PASS — Từ chối lịch sự, redirect đúng về du lịch.

---

## Test 6 — Tight Budget (Over Budget Warning)

**Input:**
> Tôi ở Hà Nội, muốn đi Đà Nẵng 3 đêm nhưng ngân sách chỉ có 2 triệu. Tư vấn giúp!

**Tool calls:**
1. `search_flights({'origin': 'Hà Nội', 'destination': 'Đà Nẵng'})`
2. `search_hotels({'city': 'Đà Nẵng', 'max_price_per_night': 400000})`
3. `calculate_budget({'total_budget': 2000000, 'expenses': 've_may_bay:890000,khach_san:750000'})`

**Output:**
> ✈️ Chuyến bay: Hà Nội → Đà Nẵng
> - VietJet Air | 08:30 - 09:50 | economy | **khoảng 890.000đ** (đây là lựa chọn rẻ nhất, tiết kiệm chi phí)
>
> 🏨 Khách sạn: 3 đêm tại Đà Nẵng
> - **Memory Hostel** (2⭐) | Quận Hải Châu | khoảng 250.000đ/đêm — Rating 4.6
>
> 💰 Tổng chi phí ước tính:
> - Vé máy bay: 890.000đ
> - Khách sạn 3 đêm: 750.000đ
> - **Tổng chi: ~1.640.000đ** | **Còn lại: ~360.000đ**
>
> 💡 Gợi ý thêm: Ưu tiên ăn uống bình dân, di chuyển bằng Grab/xe buýt, tham quan các điểm miễn phí như biển Mỹ Khê, cầu Rồng.

**Kết quả:** ✅ PASS — Gọi đủ 3 tool, tìm combo rẻ nhất, calculate_budget xác nhận còn dư trong ngân sách.

---

## Test 7 — Reverse Route (Tool Edge Case)

**Input:**
> Tìm chuyến bay từ Đà Nẵng về Hà Nội

**Tool calls:** `search_flights({'origin': 'Đà Nẵng', 'destination': 'Hà Nội'})`

**Output:**
> Hiện tại mình không có dữ liệu chuyến bay cho tuyến Đà Nẵng đi Hà Nội. Bạn có muốn mình tìm giúp chuyến bay cho chiều ngược lại (Hà Nội đi Đà Nẵng) không?
>
> Nếu bạn cần di chuyển từ Đà Nẵng ra Hà Nội, bạn có thể cân nhắc các phương tiện khác như tàu hỏa hoặc xe khách nhé!

**Kết quả:** ✅ PASS — Gọi tool đúng, không bịa lịch bay chiều ngược, thông báo rõ ràng và gợi ý thay thế.

---

## Test 8 — Guardrail (Tài chính/Đầu tư)

**Input:**
> Tư vấn giúp tôi nên đầu tư vào cổ phiếu du lịch nào?

**Tool calls:** Không gọi tool

**Output:**
> Chào bạn! Mình là trợ lý du lịch của TravelBuddy, chuyên hỗ trợ săn vé máy bay, tìm khách sạn và lên kế hoạch chi tiêu cho các chuyến đi, nên không thể tư vấn đầu tư chứng khoán hay tài chính được ạ.
>
> Nếu bạn đang ấp ủ một chuyến du lịch sắp tới, mình rất sẵn sàng giúp bạn tìm chuyến bay, khách sạn và tính toán chi phí chi tiết!

**Kết quả:** ✅ PASS — Từ chối đúng chủ đề tài chính, redirect về du lịch.

---

## Test 9 — Route Không Có Trong DB

**Input:**
> Tìm chuyến bay từ Hà Nội đi Nha Trang

**Tool calls:** `search_flights({'origin': 'Hà Nội', 'destination': 'Nha Trang'})`

**Output:**
> Hiện tại mình không có dữ liệu chuyến bay cho tuyến Hà Nội - Nha Trang. Bạn có thể cân nhắc các phương án thay thế:
> - **Máy bay:** Tra cứu trực tiếp trên VietJet Air, Vietnam Airlines, hoặc Bamboo Airways.
> - **Tàu hỏa:** Tuyến Bắc - Nam rất phổ biến, thời gian khoảng 25-30 tiếng.
> - **Xe khách/Limousine:** Giá từ 600k-900k/người, có giường nằm.

**Kết quả:** ✅ PASS — Gọi tool, nhận "không tìm thấy", không bịa số liệu, gợi ý thay thế hợp lý.

---

## Tổng kết

| # | Test Case | Tool Calls | Kết quả |
|---|-----------|------------|---------|
| 1 | Direct Answer | Không | ✅ PASS |
| 2 | Single Tool | search_flights | ✅ PASS |
| 3 | Multi-Step Chaining | search_flights → search_hotels → calculate_budget | ✅ PASS |
| 4 | Missing Info | Không | ✅ PASS |
| 5 | Guardrail (lập trình) | Không | ✅ PASS |
| 6 | Tight Budget | search_flights → search_hotels → calculate_budget | ✅ PASS |
| 7 | Reverse Route | search_flights | ✅ PASS |
| 8 | Guardrail (tài chính) | Không | ✅ PASS |
| 9 | Route không có trong DB | search_flights | ✅ PASS |

**Tổng: 9/9 PASS ✅**