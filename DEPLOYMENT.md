# Thông Tin Deploy — Checkpoint 5

## Thông Tin Học Viên

| Mục | Nội dung |
|-----|----------|
| Họ và tên | PHẠM THANH HƯNG |
| Mã học viên | 01468 |
| Repo | https://github.com/ThanhHungtaptanhhocpython/K4-Day12-2A202601468-PhamThanhHung |

## Service

| Mục | Nội dung |
|-----|----------|
| Public URL | https://day12-chat-nnuj.onrender.com |
| Platform | Render |
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
curl -i https://day12-chat-nnuj.onrender.com/healthz

# 2. Readiness — mong đợi 200 {"status":"ready"} (đã nối được Redis)
curl -i https://day12-chat-nnuj.onrender.com/readyz

# 3. Không có token — mong đợi 401 kèm header WWW-Authenticate
curl -i -X POST https://day12-chat-nnuj.onrender.com/chat \
  -H "Content-Type: application/json" \
  -d '{"message":"Hello"}'

# 4. Có token — mong đợi 200 kèm câu trả lời
curl -i -X POST https://day12-chat-nnuj.onrender.com/chat \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $API_TOKEN" \
  -H "X-Client-Id: sv-test" \
  -d '{"message":"Deploy là gì?"}'

# 5. Rate limit — gọi 15 lần, những lần cuối phải trả 429
for i in $(seq 1 15); do
  curl -s -o /dev/null -w "%{http_code} " -X POST https://day12-chat-nnuj.onrender.com/chat \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $API_TOKEN" \
    -H "X-Client-Id: sv-test" \
    -d '{"message":"test"}'
done; echo
```

## Kết Quả Chạy Thật

```
{"status":"ok","service":"day12-chat-service","version":"1.0.0"}

{"status":"ready","redis":true}

{"detail":"invalid or missing bearer token"}

{"reply":"Ngắn gọn: hello phụ thuộc vào ba yếu tố — cấu hình qua biến môi trường, health check để orchestrator biết trạng thái, và giới hạn tài nguyên.","client_id":"anonymous","turns_before":0,"usd_cost":2.115e-05,"usage":{"prompt":1,"completion":35}}
```

## Ảnh Chụp Màn Hình

Đặt ảnh trong thư mục `screenshots/`:
- `screenshots/dashboard.png`
- `screenshots/healthz.png`
- `screenshots/curl_test.png`
