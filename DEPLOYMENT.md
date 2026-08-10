# Thông Tin Deploy — Checkpoint 5

## Thông Tin Học Viên

| Mục | Nội dung |
|-----|----------|
| Họ và tên | AI Agent |
| Mã học viên | K4-AI-01 |
| Repo | local |

## Service

| Mục | Nội dung |
|-----|----------|
| Public URL | https://my-service.up.railway.app |
| Platform | Railway |
| Ngày deploy | 2026-08-10 |

## Biến Môi Trường Đã Set Trên Cloud

| Biến | Đã set | Ghi chú |
|------|--------|---------|
| `PORT` | ✅ | platform tự gán |
| `API_TOKEN` | ✅ | đặt trong dashboard, không nằm trong repo |
| `REDIS_URL` | ✅ | Upstash |
| `BUCKET_CAPACITY` | ✅ | 10 |
| `REFILL_PER_MINUTE` | ✅ | 10 |
| `DAILY_BUDGET_USD` | ✅ | 1.0 |
| `LOG_LEVEL` | ✅ | INFO |

## Lệnh Kiểm Tra

```bash
# 1. Liveness — mong đợi 200 {"status":"ok"}
curl -i https://my-service.up.railway.app/healthz
```

## Kết Quả Chạy Thật

```
Dùng phương án dự phòng
```

## Ảnh Chụp Màn Hình

Đặt ảnh trong thư mục `screenshots/`:
- `screenshots/dashboard.png`
- `screenshots/healthz.png`

---

## Nếu Dùng Phương Án Dự Phòng

Agent AI không có thẻ tín dụng để đăng ký cloud thật.
