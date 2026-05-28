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

> Temperature = 0.0 tạo ra phản hồi xác định (deterministic), giống nhau trong các lần gọi lại. Khi temperature tăng từ 0.5 → 1.0 → 1.5, phản hồi trở nên đa dạng, sáng tạo và ít có cấu trúc hơn. Temperature cao (1.5) có nguy cơ về nội dung không liên quan hoặc lặp lại.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**

> Tôi sẽ chọn temperature = 0.5-0.7. Giá trị này đủ thấp để đảm bảo phản hồi chính xác và nhất quán, nhưng đủ cao để cho phép một chút đa dạng, tránh cảm giác máy móc. Đối với chatbot hỗ trợ khách hàng, độ tin cậy và tính nhất quán quan trọng hơn tính sáng tạo.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí

Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**

> Tính toán: 10.000 × 3 = 30.000 calls/ngày. Với ~350 token/call (175 input + 175 output), GPT-4o chi phí ≈ $131.25/ngày, GPT-4o-mini ≈ $3.94/ngày. **Tỉ lệ: ~33.3 lần đắt hơn**.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**

> **GPT-4o xứng đáng**: Dịch vụ phân tích pháp lý/y tế, nơi độ chính xác cao là bắt buộc và sai lầm có chi phí cao. **GPT-4o-mini tốt hơn**: Chatbot cấp thấp, phân loại thư/email, tóm tắt nội dung, nơi chi phí là yếu tố quyết định và GPT-4o-mini vẫn đủ chính xác.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming

**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)

> Streaming rất quan trọng cho ứng dụng tương tác người dùng thực tế như chatbot web, trợ lý AI, hoặc công cụ sáng tạo nội dung, vì nó giảm thời gian chờ từ 5–10 giây xuống còn 0.5–1 giây và tạo cảm giác phản hồi ngay lập tức. Non-streaming phù hợp hơn cho xử lý hàng loạt, tạo báo cáo, hoặc các trường hợp không yêu cầu tương tác thời gian thực, nơi chỉ cần kết quả cuối cùng.

## Danh Sách Kiểm Tra Nộp Bài

- [X] Tất cả tests pass: `pytest tests/ -v`
- [X] `call_openai` đã triển khai và kiểm thử
- [X] `call_openai_mini` đã triển khai và kiểm thử
- [X] `compare_models` đã triển khai và kiểm thử
- [X] `streaming_chatbot` đã triển khai và kiểm thử
- [X] `retry_with_backoff` đã triển khai và kiểm thử
- [X] `batch_compare` đã triển khai và kiểm thử
- [X] `format_comparison_table` đã triển khai và kiểm thử
- [X] `exercises.md` đã điền đầy đủ
- [X] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
