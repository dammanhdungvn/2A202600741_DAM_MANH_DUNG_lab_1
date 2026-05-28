# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng, câu trả lời đa dạng và sáng tạo hơn, nhưng mức độ nhất quán giảm và có thể thêm chi tiết không chắc chắn. Ở temperature thấp (0.0) phản hồi ổn định và giống nhau giữa các lần gọi. Ở mức cao (1.0–1.5) phong cách diễn đạt phong phú hơn nhưng dễ lệch khỏi yêu cầu hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi chọn khoảng 0.2–0.4 để ưu tiên tính chính xác và nhất quán, tránh trả lời ngẫu hứng. Mức này vẫn đủ linh hoạt để diễn đạt tự nhiên mà không làm tăng rủi ro sai lệch thông tin.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> 10.000 * 3 * 350 = 10,5 triệu token. GPT-4o: 10,5M/1K * $0.010 ≈ $105; GPT-4o-mini: 10,5M/1K * $0.0006 ≈ $6.3. Như vậy GPT-4o đắt hơn khoảng 16,7 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi cần suy luận phức tạp, xử lý yêu cầu nhiều bước, hoặc hỗ trợ quyết định quan trọng (ví dụ: tư vấn chuyên môn có kiểm soát chất lượng). GPT-4o-mini phù hợp cho FAQ, tóm tắt nội dung ngắn, phân loại yêu cầu, hoặc trợ lý nội bộ nơi chi phí và tốc độ quan trọng hơn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng đang chờ tương tác, vì giúp giảm cảm giác trễ và cải thiện trải nghiệm thời gian thực (chat, hỗ trợ trực tuyến, viết nội dung). Non-streaming phù hợp khi câu trả lời ngắn, cần hậu xử lý/kiểm tra toàn bộ trước khi trả về, hoặc chạy theo lô để tối ưu hóa chi phí và log.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
