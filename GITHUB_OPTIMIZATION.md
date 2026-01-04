# GitHub 仓库优化 TODO

> 仓库: https://github.com/tukuaiai/tradecat
> 当前状态: ⭐ 377 | 🍴 118 | 社区健康度 71%

---

## 🔴 高优先级

### 1. 添加 Topics 标签
**影响**: 搜索曝光 +50%

在 GitHub 仓库页面 → Settings → 右侧 "Topics" 添加：
```
python, trading, cryptocurrency, binance, quantitative-trading, 
telegram-bot, timescaledb, technical-analysis, market-data, 
crypto-trading, ta-lib, ccxt, asyncio, pandas
```

### 2. 创建 Release 版本
**影响**: 用户信任度提升，方便追踪稳定版本

```bash
# 创建 tag
git tag -a v1.0.0 -m "🎉 首个正式版本"
git push origin v1.0.0

# 然后在 GitHub Releases 页面编辑，添加 changelog
```

Release 内容建议：
- 6 个微服务架构
- 38 个技术指标
- 3.73 亿条 K 线数据支持
- Telegram Bot 集成
- AI 分析 (Wyckoff 方法论)

---

## 🟡 中优先级

### 3. 添加 Issue 模板
**影响**: 社区健康度 71% → 85%

创建 `.github/ISSUE_TEMPLATE/bug_report.md`:
```markdown
---
name: Bug 报告
about: 报告问题帮助我们改进
title: '[BUG] '
labels: bug
assignees: ''
---

**问题描述**
简要描述遇到的问题

**复现步骤**
1. 执行 '...'
2. 运行 '...'
3. 出现错误

**期望行为**
描述你期望发生的情况

**环境信息**
- OS: [e.g. Ubuntu 22.04 / WSL2]
- Python: [e.g. 3.12]
- 服务: [e.g. telegram-service]

**日志/截图**
如有相关日志或截图请附上
```

创建 `.github/ISSUE_TEMPLATE/feature_request.md`:
```markdown
---
name: 功能建议
about: 提出新功能或改进建议
title: '[FEAT] '
labels: enhancement
assignees: ''
---

**功能描述**
简要描述你希望添加的功能

**使用场景**
描述这个功能解决什么问题

**可能的实现方案**
如果有想法，描述可能的实现方式
```

### 4. 添加 PR 模板
**影响**: 社区健康度 → 100%

创建 `.github/PULL_REQUEST_TEMPLATE.md`:
```markdown
## 变更说明
简要描述本次 PR 的改动

## 变更类型
- [ ] Bug 修复
- [ ] 新功能
- [ ] 文档更新
- [ ] 重构
- [ ] 其他

## 检查清单
- [ ] 代码已自测通过
- [ ] 已更新相关文档
- [ ] 已运行 `./scripts/verify.sh`

## 关联 Issue
closes #
```

---

## 🟢 低优先级

### 5. 添加 GitHub Actions CI
**影响**: 代码质量自动保障

创建 `.github/workflows/ci.yml`:
```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.12'
      - name: Install ruff
        run: pip install ruff
      - name: Lint
        run: ruff check services/

  verify:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Syntax check
        run: python3 -m py_compile services/*/src/*.py
```

### 6. 添加更多 README Badges
在 README.md 顶部添加：
```markdown
![GitHub Actions](https://github.com/tukuaiai/tradecat/workflows/CI/badge.svg)
![GitHub release](https://img.shields.io/github/v/release/tukuaiai/tradecat)
![GitHub last commit](https://img.shields.io/github/last-commit/tukuaiai/tradecat)
```

### 7. 启用 GitHub Pages (可选)
用于托管项目文档站点，可基于 README 自动生成。

---

## ✅ 完成检查

- [ ] Topics 已添加
- [ ] v1.0.0 Release 已创建
- [ ] Issue 模板已添加
- [ ] PR 模板已添加
- [ ] GitHub Actions 已配置
- [ ] README Badges 已更新
- [ ] 社区健康度达到 100%
