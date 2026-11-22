# Mysterio Claude Agent Marketplace

Marketplace nội bộ phân phối Claude Code plugin. Plugin `agent-framework` cung cấp agents theo mô hình Opus / Sonnet / Haiku và các skill gọi workflow.

## Cài một lần cho từng project

Trong terminal tại thư mục project cần cài:

```bash
claude plugin marketplace add YOUR_GITHUB_OWNER/claude-agent-marketplace --scope project
claude plugin install agent-framework@mysterio-dev-tools --scope project
```

Thay `YOUR_GITHUB_OWNER/claude-agent-marketplace` bằng GitHub owner/repository thực tế.

Sau khi cài, trong Claude Code chạy:

```text
/agent-framework:workflow
```

Để thiết lập kiểm thử:

```text
/agent-framework:e2e
```

Để review thay đổi hiện tại:

```text
/agent-framework:review
```

## CLI tương đương

```bash
claude plugin marketplace add YOUR_GITHUB_OWNER/claude-agent-marketplace --scope project
claude plugin install agent-framework@mysterio-dev-tools --scope project
claude plugin list
```

Cập nhật marketplace/plugin:

```bash
claude plugin marketplace update mysterio-dev-tools
claude plugin update agent-framework@mysterio-dev-tools
```

Gỡ:

```bash
claude plugin uninstall agent-framework@mysterio-dev-tools --scope project
claude plugin marketplace remove mysterio-dev-tools
```

Nếu phiên bản Claude Code không nhận `plugin update`, mở `/plugin`, vào Installed và chọn Update.

## Agent roster

| Agent | Model | Quyền / nhiệm vụ |
|---|---|---|
| `reviewer` | Opus | Review độc lập, chỉ đọc |
| `security-reviewer` | Opus | Security audit, chỉ đọc |
| `code-developer` | Sonnet | Implement và sửa lỗi |
| `e2e-engineer` | Sonnet | Thiết kế/viết API và browser E2E |
| `explorer` | Haiku | Khám phá codebase, chỉ đọc |
| `test-runner` | Haiku | Chạy kiểm thử và báo cáo |

## Lưu ý

- Plugin được cài theo project scope, nhưng file plugin nằm trong cache Claude Code; không copy agent files vào repository.
- Marketplace/project settings được khai báo bởi Claude Code khi cài.
- Với private GitHub repository, người cài cần quyền clone repository.
- Framework không tự giả định stack, test command, database hoặc server port. Skill sẽ yêu cầu agent khám phá repo trước.
- API/browser E2E không thay thế kiểm thử native-only như IAP, push permission, Live Activities, camera hoặc tích hợp OS.
