# Case-study to learn GitHub Actions - CICD

Đây là một dự án Node.js đơn giản được tạo ra với mục đích **học cách sử dụng GitHub Actions** để thiết lập quy trình kiểm tra (CI – Continuous Integration) cơ bản.  
Dự án **không triển khai (deploy)**, chỉ chạy kiểm thử tự động khi code được đẩy lên GitHub.

## Mục tiêu

- Thiết lập quy trình kiểm thử tự động với GitHub Actions
- Tự động chạy `npm install` và `npm test` sau mỗi lần push code lên branch `main`
- Làm quen với CI trước khi học CI/CD hoàn chỉnh

---

## Cấu trúc thư mục

```

.
├── .github/
│   └── workflows/
│       └── ci.yml         # Workflow GitHub Actions để kiểm thử
├── src/                   # Mã nguồn chính
├── test/                  # Thư mục chứa các test (nếu có)
├── package.json
└── README.md

````

---

## Cách sử dụng

### 1. Clone repository

```bash
git clone https://github.com/limbanga/learn-github-action
cd learn-github-action
````

### 2. Cài đặt thư viện

```bash
npm install
```

### 3. Chạy ứng dụng

```bash
npm start
```

### 4. Chạy kiểm thử thủ công

```bash
npm test
```

---

## GitHub Actions – `ci-cd.yml`

Workflow sẽ tự động chạy khi bạn push code lên `main`.

```yaml
# .github/workflows/ci-cd.yml
name: CI for Node.js

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

---

## Tài liệu tham khảo

* [GitHub Actions Documentation](https://docs.github.com/en/actions)
* [Node.js Documentation](https://nodejs.org/en/docs)

---

## Giấy phép

Dự án này được phát hành theo giấy phép MIT.




