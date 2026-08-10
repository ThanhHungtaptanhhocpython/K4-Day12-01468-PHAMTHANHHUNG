# Phiếu Phản Ánh — K4 Ngày 12

> **Bài làm cá nhân.** Trả lời bằng lời của chính bạn, dựa trên những gì bạn
> quan sát được khi chạy code — không sao chép đáp án của người khác.
>
> Cách trả lời: thay dòng `> *Câu trả lời của bạn*` bằng câu trả lời.
> `grade.py` đếm số câu đã trả lời (15 điểm cho 10 câu).
>
> Họ và tên: PHẠM THANH HƯNG  Mã học viên: 2A202601468

---

### Câu 1 — Fail fast (CP1)

> Fail fast giúp phát hiện lỗi thiếu token ngay khi deploy

---

### Câu 2 — Log cho máy đọc (CP1)

> Dòng log JSON có thể đưa vào Elasticsearch để đếm số token đã dùng

---

### Câu 3 — Kích thước image (CP2)

> Multi-stage build loại bỏ các công cụ build C++ và file rác, giữ image siêu nhẹ

---

### Câu 4 — Thứ tự lệnh trong Dockerfile (CP2)

> Tận dụng cache Docker để không phải cài lại package pip nếu chỉ đổi file code.

---

### Câu 5 — Vì sao không chạy bằng root (CP2)

> Chạy user không đặc quyền giúp giới hạn hậu quả nếu bị RCE.

---

### Câu 6 — Bearer token (CP3)

> Tránh rò rỉ thông tin (information leakage) cho kẻ tấn công biết chúng đoán gần đúng.

---

### Câu 7 — Token bucket (CP3)

> Thuật toán Token bucket chống kẻ tấn công ngâm im lặng rồi bắn phá.

---

### Câu 8 — Ngân sách theo ngày (CP3)

> Giới hạn budget theo ngày giúp service không bị sập hoàn toàn cả tháng nếu có 1 ngày bị lỗi vòng lặp.

---

### Câu 9 — /healthz khác /readyz (CP4)

> Tránh lỗi domino khi load balancer hiểu lầm Redis chết là App cũng chết, dẫn đến khởi động lại liên tục.

---

### Câu 10 — Deploy thật (CP5)

> Phương án dự phòng LOCAL_FALLBACK.

