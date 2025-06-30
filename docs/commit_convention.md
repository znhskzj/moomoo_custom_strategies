# Conventional Commits 规范指南

## 提交格式
```
<type>[(optional scope)]: <description>

[optional body]

[optional footer(s)]
```

## 主要提交类型 (Type)

### 主版本号 (MAJOR Version - Breaking Changes)
- `BREAKING CHANGE:` 在提交信息的 footer 中标注
- 任何带有 `!` 的提交，例如：`feat!:` 或 `fix!:`

### 次版本号 (MINOR Version - Features)
- `feat:` 新功能或特性
  - 例：新增策略功能、新增技术指标

### 修订号 (PATCH Version - Bug Fixes & Small Changes)
- `fix:` 修复 bug
- `perf:` 性能优化
- `refactor:` 代码重构（不改变功能）
- `style:` 代码格式修改
- `test:` 测试用例相关修改

### 不影响版本号
- `docs:` 文档更新
- `chore:` 构建过程或辅助工具的变动
- `ci:` CI/CD 相关变更
- `build:` 影响构建系统或外部依赖

## Scope 使用规范
策略相关改动建议使用以下 scope：
- `strategy` - 整体策略逻辑
- `grid` - 网格交易相关
- `position` - 持仓管理
- `order` - 订单管理
- `risk` - 风险控制
- `config` - 配置相关

## 示例

### 重大更新
```
feat!: change grid trading core algorithm

BREAKING CHANGE: grid calculation now uses different parameters
```

### 新功能
```
feat(strategy): add new position management system
```

### Bug 修复
```
fix(order): correct order quantity calculation
```

### 文档更新
```
docs: update project documentation for v5.3.8

- Update changelog with v5.3.8 features and fixes
- Enhance README with latest version features and directory structure
- Improve overview.md with detailed project description and functionalities
```

### 代码重构
```
refactor(grid): simplify grid reset logic
```

### 性能优化
```
perf(position): optimize position verification process
```

### 配置修改
```
chore(config): update trading parameters
```

## 自动版本号更新规则

1. MAJOR（主版本号）更新条件：
   - 包含 `BREAKING CHANGE:` 注释
   - 类型带有 `!` 符号

2. MINOR（次版本号）更新条件：
   - 类型为 `feat:`

3. PATCH（修订号）更新条件：
   - 类型为 `fix:`, `perf:`, `refactor:`

4. 不触发版本更新：
   - 类型为 `docs:`, `style:`, `test:`, `chore:`, `ci:`, `build:`

## CI/CD 配置建议

1. 版本号管理:
```yaml
version-management:
  rules:
    - breaking: major
    - type: feat
      bump: minor
    - type: fix
      bump: patch
    - type: perf
      bump: patch
    - type: refactor
      bump: patch
```

2. CHANGELOG 生成:
```yaml
changelog:
  sections:
    - group: "💥 Breaking Changes"
      types: ["BREAKING CHANGE"]
    - group: "✨ New Features"
      types: ["feat"]
    - group: "🐛 Bug Fixes"
      types: ["fix"]
    - group: "♻️ Refactors"
      types: ["refactor"]
    - group: "⚡ Performance"
      types: ["perf"]
    - group: "📚 Documentation"
      types: ["docs"]
    - group: "🔧 Maintenance"
      types: ["chore"]
```