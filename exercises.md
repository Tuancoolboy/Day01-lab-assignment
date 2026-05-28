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

**Kết quả chạy `python template.py`:**

![Kết quả so sánh GPT-4o và GPT-4o-mini](https://drive.google.com/thumbnail?id=116tzkiqR6FeClYkWoiutzD55oZtmi8q_&sz=w1000)

[Xem ảnh trên Google Drive](https://drive.google.com/file/d/116tzkiqR6FeClYkWoiutzD55oZtmi8q_/view?usp=sharing)

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít thay đổi giữa các lần gọi. Khi tăng lên 0.5 và 1.0, câu trả lời đa dạng hơn, cách diễn đạt tự nhiên hơn và có thể chọn các sự thật khác nhau. Ở mức 1.5, phản hồi sáng tạo hơn nhưng cũng dễ lan man hoặc có nguy cơ kém chính xác hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2-0.4 cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời nhất quán, ít bịa đặt và vẫn đủ tự nhiên để giao tiếp với người dùng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload mỗi ngày là 10.000 x 3 x 350 = 10.500.000 token, tương đương 10.500 nhóm 1K token. Theo chi phí trong đề bài, GPT-4o tốn khoảng 10.500 x $0.010 = $105/ngày, còn GPT-4o-mini tốn khoảng 10.500 x $0.0006 = $6.30/ngày. Vì vậy GPT-4o đắt hơn GPT-4o-mini khoảng 105 / 6.30 = 16.7 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o đáng dùng khi tác vụ cần chất lượng suy luận cao, ví dụ phân tích tài liệu phức tạp, tư vấn kỹ thuật, xử lý yêu cầu quan trọng hoặc cần độ chính xác tốt hơn. GPT-4o-mini phù hợp hơn cho các tác vụ số lượng lớn, chi phí nhạy cảm và tương đối đơn giản như phân loại câu hỏi, tóm tắt ngắn, chatbot FAQ hoặc phản hồi hỗ trợ cơ bản.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang trả lời ngay, ví dụ chatbot, trợ lý viết nội dung, giải thích bài học hoặc tạo báo cáo dài. Việc hiển thị từng phần giúp giảm cảm giác chờ đợi và làm trải nghiệm giống hội thoại thật hơn. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý toàn bộ kết quả trước khi hiển thị, hoặc khi hệ thống cần validate, format JSON, lưu log hay kiểm tra an toàn trước khi trả câu trả lời cho người dùng.


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
