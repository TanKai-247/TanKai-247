# SETUP GUIDE

## 1) Profile repository

Repository này phải có đúng dạng:

```text
YOUR_USERNAME/YOUR_USERNAME
```

Ví dụ username GitHub của bạn là `tankhai123` thì repository profile phải là:

```text
tankhai123/tankhai123
```

## 2) Copy file

Sao chép các file này vào repo profile của bạn:

```text
.
├── README.md
├── assets/
│   └── profile-header.svg
└── .github/
    └── workflows/
        ├── profile-visuals.yml
        └── metrics.yml
```

## 3) Replace username

Tìm tất cả chữ:

```text
YOUR_USERNAME
```

và thay bằng username GitHub thật của bạn.

## 4) Vì sao mình đã fix lỗi ảnh / hiệu ứng chưa hiển thị?

Mình đã sửa theo hướng ổn định hơn:

- Dùng `raw.githubusercontent.com` cho ảnh trong README
- Dùng tên file snake thống nhất giữa workflow và README
- Dùng cron UTC chuẩn để tránh lỗi schedule không chạy
- Chuyển banner sang SVG an toàn, không phụ thuộc animation dễ bị GitHub chặn
- Giữ hiệu ứng glow và bố cục đẹp nhưng ổn định hơn khi render

## 5) Secret cần tạo

Workflow `Metrics` cần secret:

```text
METRICS_TOKEN
```

Tạo tại:

```text
Repository Settings → Secrets and variables → Actions → New repository secret
```

Nếu chưa muốn dùng metrics thì bạn có thể xóa:
- `.github/workflows/metrics.yml`
- phần `GitHub Overview` trong `README.md`

## 6) Chạy workflow

Sau khi push code:

1. Vào tab **Actions**
2. Chạy `Build Profile Visuals`
3. Chạy `Metrics`

## 7) Nếu snake hoặc 3D graph chưa hiện

Kiểm tra:
- repo profile là public
- đã thay hết `YOUR_USERNAME`
- workflow chạy thành công
- branch `output` đã được tạo
- file `github-metrics.svg` và thư mục `profile-3d-contrib/` đã xuất hiện trên branch `main`
