# srs-ag10-functional-spec

**AG-10** · Agent Node · phiên bản **1.0.0** · giấy phép MIT

> Vietnamese-language Claude skill — one independent, reusable service of the SRS-SOP agent pipeline. Machine-readable contract: [`skill.json`](skill.json).

Agent Node AG-10 (Pha B SOP): đặc tả Use Case theo Use-Case 3.0, hai mức fidelity (brief trong vòng lặp → detailed khi hội tụ); làm chủ ngữ nghĩa field; luồng, Special Requirements, Use-Case Slice, phân quyền hai chiều, Gherkin; nguồn cho TL-03/TL-12/TL-05.

## Hợp đồng giao tiếp

Skill là một dịch vụ độc lập, ghép lỏng: nhận đầu vào và trả đầu ra dưới dạng tài liệu/JSON mô tả trong [`SKILL.md`](SKILL.md), không gọi trực tiếp skill khác và không gắn với dự án cụ thể. Dùng riêng lẻ, hoặc ghép qua bộ điều phối [`srs-sop-pipeline`](https://github.com/HaNguyen1409/srs-sop-pipeline).

| Bước SOP | Việc | Loại | Nhận từ | Chuyển tới |
|---|---|---|---|---|
| 10 | Đặc tả UC (fidelity brief→detailed, screen-agnostic vòng đầu; làm chủ ngữ nghĩa field) | Agent | B9; vòng ≥ 2: B17 | B11, B14, (B-GHERKIN/B-PERM) |
| 18 | HỘI TỤ: chốt UC 3.0 đầy đủ + ERD logical chốt + đối chiếu UC ↔ ERD ↔ prototype đã duyệt | Human Gate | B17, B10, B11, B12 | B19, B20 |

**Skill phía trước (cấp đầu vào):** [`srs-ag06-business-model`](https://github.com/HaNguyen1409/srs-ag06-business-model) `^1.5.0` · [`srs-ag09-demo-feedback-triage`](https://github.com/HaNguyen1409/srs-ag09-demo-feedback-triage) `^1.0.0` · [`srs-ag14-data-design`](https://github.com/HaNguyen1409/srs-ag14-data-design) `^1.0.0` · [`srs-ag07-screen-flow-design`](https://github.com/HaNguyen1409/srs-ag07-screen-flow-design) `^1.0.0`

**Skill phía sau (dùng đầu ra):** [`srs-ag14-data-design`](https://github.com/HaNguyen1409/srs-ag14-data-design) `^1.0.0` · [`srs-ag11-nfr-spec`](https://github.com/HaNguyen1409/srs-ag11-nfr-spec) `^1.0.0`

## Cài đặt

**Claude Code** — clone đúng phiên bản vào thư mục skill:

```bash
git clone --branch v1.0.0 https://github.com/HaNguyen1409/srs-ag10-functional-spec.git ~/.claude/skills/srs-ag10-functional-spec
```

Nâng cấp: `git -C ~/.claude/skills/srs-ag10-functional-spec fetch --tags && git -C ~/.claude/skills/srs-ag10-functional-spec checkout v<phiên-bản-mới>`.

**claude.ai / Claude Desktop** — tải `srs-ag10-functional-spec-v1.0.0.zip` ở trang [Releases](https://github.com/HaNguyen1409/srs-ag10-functional-spec/releases) rồi tải lên ở phần Skills trong cài đặt.

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
