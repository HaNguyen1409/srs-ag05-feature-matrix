# srs-ag05-feature-matrix

**AG-05** · Agent Node · phiên bản **2.0.0** · giấy phép MIT

> Vietnamese-language Claude skill — one independent, reusable service of the SRS-SOP agent pipeline. Machine-readable contract: [`skill.json`](skill.json).

[Bước tuỳ chọn] Agent Node AG-05 (Bước B8 SOP viết SRS): lập ma trận tính năng × sản phẩm và danh sách đề xuất bổ sung MKT có căn cứ, chấm giá trị/công sức/rủi ro phình phạm vi (điểm nguyên), gợi ý MoSCoW, chờ khách xác nhận qua demo. Code Node DET-08b tính điểm & áp trần.

## Hợp đồng giao tiếp

Skill là một dịch vụ độc lập, ghép lỏng: nhận đầu vào và trả đầu ra dưới dạng tài liệu/JSON mô tả trong [`SKILL.md`](SKILL.md), không gọi trực tiếp skill khác và không gắn với dự án cụ thể. Dùng riêng lẻ, hoặc ghép qua bộ điều phối [`srs-sop-pipeline`](https://github.com/HaNguyen1409/srs-sop-pipeline).

| Bước SOP | Việc | Loại | Nhận từ | Chuyển tới |
|---|---|---|---|---|
| 8 | (Tuỳ chọn) Ma trận tính năng & đề xuất bổ sung | Agent | B5, B6, B7, (B5a) | B8a, B9 |

**Sản phẩm đầu ra:** none (MKT proposals + feature matrix)

**Skill phía trước (cấp đầu vào):** [`srs-ag03-gap-analysis`](https://github.com/HaNguyen1409/srs-ag03-gap-analysis) `^2.2.1` · [`srs-ag04-competitor-research`](https://github.com/HaNguyen1409/srs-ag04-competitor-research) `^2.0.0` · [`srs-agmt-functional-matrix`](https://github.com/HaNguyen1409/srs-agmt-functional-matrix) `^1.1.0`

**Skill phía sau (dùng đầu ra):** [`srs-agtq-project-overview`](https://github.com/HaNguyen1409/srs-agtq-project-overview) `^1.1.0` · [`srs-ag06-business-model`](https://github.com/HaNguyen1409/srs-ag06-business-model) `^1.4.2`

## Cài đặt

**Claude Code** — clone đúng phiên bản vào thư mục skill:

```bash
git clone --branch v2.0.0 https://github.com/HaNguyen1409/srs-ag05-feature-matrix.git ~/.claude/skills/srs-ag05-feature-matrix
```

Nâng cấp: `git -C ~/.claude/skills/srs-ag05-feature-matrix fetch --tags && git -C ~/.claude/skills/srs-ag05-feature-matrix checkout v<phiên-bản-mới>`.

**claude.ai / Claude Desktop** — tải `srs-ag05-feature-matrix-v2.0.0.zip` ở trang [Releases](https://github.com/HaNguyen1409/srs-ag05-feature-matrix/releases) rồi tải lên ở phần Skills trong cài đặt.

**Cả bộ** — xem [`srs-sop-skills`](https://github.com/HaNguyen1409/srs-sop-skills) (cài toàn bộ skill theo phiên bản đã khoá).

## Quản lý phiên bản

Theo [SemVer](https://semver.org/lang/vi/), áp cho hợp đồng giao tiếp của skill:

| Tăng | Khi |
|---|---|
| MAJOR | Đổi hợp đồng làm vỡ skill phía sau: đổi/bỏ trường JSON, đổi hệ mã ID, đổi bố cục tài liệu đầu ra |
| MINOR | Thêm khả năng tương thích ngược: trường tuỳ chọn, mục mới, chế độ mới |
| PATCH | Sửa câu chữ, sửa lỗi, làm rõ luật mà không đổi đầu ra |

Phát hành: sửa `SKILL.md` → tăng `version` trong frontmatter, `VERSION`, `skill.json` → thêm mục vào [`CHANGELOG.md`](CHANGELOG.md) → `python tools/check_skill.py` → commit → `git tag -a vX.Y.Z -m "vX.Y.Z"` → `git push --follow-tags`. GitHub Actions kiểm lại, chạy test và đính kèm zip vào Release.

## Giấy phép

MIT — xem [`LICENSE`](LICENSE).
