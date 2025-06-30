# moomoo_custom_strategies

This repository contains version-controlled custom quantitative strategies for the moomoo client

本项目包含基于网格交易原则实现的多个量化策略。每个策略具有不同的参数和应用场景。

## ⚠️ 免责声明 | Disclaimer

### 中文声明

本项目仅供学习和研究使用，不构成任何投资建议或交易指导。请注意：

1. 作者不是专业的投资顾问或理财规划师，本项目中的所有策略均基于个人研究和实践经验。
2. 量化交易存在固有风险，包括但不限于市场风险、流动性风险、技术风险等。
3. 任何人使用本项目中的代码进行实盘交易需自行承担全部风险和后果。
4. 策略的历史表现不代表未来收益，任何基于本项目进行的交易决策需要使用者自行判断和负责。
5. 在使用本项目代码进行实盘交易前，强烈建议：
   - 充分了解量化交易的原理和风险
   - 仔细阅读并理解代码的具体实现
   - 使用模拟盘进行充分测试
   - 根据个人风险承受能力调整参数
   - 合理控制仓位和资金规模

### English Disclaimer

This project is for educational and research purposes only. Please be aware:

1. The author is not a professional financial advisor, and all strategies are based on personal research and experience.
2. Quantitative trading involves inherent risks, including but not limited to market risk, liquidity risk, and technical risk.
3. Anyone who uses the code in this project for live trading does so at their own risk and is solely responsible for any consequences.
4. Past performance does not guarantee future results. All trading decisions based on this project require users' own judgment and responsibility.
5. Before using this code for live trading, it is strongly recommended to:
   - Fully understand the principles and risks of quantitative trading
   - Carefully read and understand the code implementation
   - Conduct thorough testing using paper trading
   - Adjust parameters according to personal risk tolerance
   - Maintain reasonable position and capital management

## 策略总览

### 策略三（V3）

- 高级网格交易策略，统一网格间距与盈利标准
- 线程安全的持仓与订单管理
- 支持批量订单执行与高频行情
- 完善的持仓验证与自动修正
- 详细日志与健壮异常处理
- 隔离模式（默认开启）：策略可独立于实际持仓运行
- 严格的价格区间风控
- 金字塔加仓（递进加仓）支持
- 所有文档、风险、参数说明集中在README
- **最新版本：v5.3.10**

### 策略二（V2）

- 标准网格交易策略，简化网格重置逻辑
- 支持批量持仓跟踪与恢复
- 改进的订单与持仓管理
- 基础风控与错误处理
- 适合需要经典网格、适度自动化的用户

### 策略一（V1）

- 基础定投（DCA）与回撤加仓策略
- 支持周期性定投和简单技术指标
- 回撤触发自动加仓
- 简单的全局参数配置
- 基础持仓跟踪与日志
- 适合初学者和简单自动投资场景

---

## Strategy Overview

### [Strategy V3](./strategies/strategy_v3/readme.md)

- Advanced grid trading strategy with unified grid intervals and profit standards
- Thread-safe position and order management
- Batch order execution and high-frequency trading support
- Comprehensive position verification and auto-correction
- Detailed logging and robust error handling
- Isolation mode (default ON): strategy can run independently of actual holdings
- Strict price range control for risk management
- Pyramid (progressive) position adding supported
- All documentation, risks, and parameters centralized in README
- **Latest version: v5.3.10**

### [Strategy V2](./strategies/strategy_v2/readme.md)

- Standard grid trading strategy with simplified grid reset logic
- Supports batch position tracking and recovery
- Improved order and position management
- Basic risk control and error handling
- Suitable for users needing classic grid trading with moderate automation

### [Strategy V1](./strategies/strategy_v1/readme.md)

- Basic DCA (Dollar-Cost Averaging) and drawdown-based adding strategy
- Periodic investment and simple technical indicator support
- Drawdown-based position scaling (auto adding on dips)
- Simple global variable and parameter configuration
- Basic position tracking and logging
- Suitable for beginners and simple automated investing scenarios

## 工具集成

项目包含多个辅助工具，位于 `tools/` 目录：

- `field_inspector.moo`: 字段检查和验证工具
- `order_analyzer.moo`: 订单分析和统计工具
- `pricedata_collector.moo`: 价格数据采集工具

## 文档结构

- `docs/`: 项目文档目录
  - `overview.md`: 项目概述和设计理念
  - `changelog.md`: 版本更新记录
  - `manual/`: 使用手册与详细说明
- `historical_orders/`: 历史订单记录
- `strategies/`: 策略实现目录
  - `strategy_v3/`: 最新的网格交易策略（v5.3.10），支持隔离模式和价格区间限制
  - `strategy_v2/`: 简化版网格交易策略
  - `strategy_v1/`: 基础网格交易策略
- `tools/`: 工具集目录

## 版本控制

每个策略版本都有独立的目录和配置文件，便于进行版本管理和策略回溯。详细的更新记录请参考 [changelog](./docs/changelog.md)。

## 最新更新（v5.3.10）

- v5.3.10：
  - 增强价格区间控制，买卖操作均严格受区间约束，支持动态调整参数
  - 优化高位网格盈利检查与批量卖出逻辑，提升止盈响应速度
  - 精简和统一全部代码注释，所有风险、历史、参数说明迁移至README，提升可维护性
  - 完善异常处理与日志输出，便于排查极端行情下的持仓与订单问题
- v5.3.9：
  - 优化批量卖出与批量持仓更新机制，提高高频行情下的执行效率
  - 增强订单确认健壮性，减少极端行情下的持仓偏差
- v5.3.8及以前：
  - 默认启用隔离模式，更好地处理持仓同步问题
  - 增加价格区间限制功能，增强风险控制
  - 改进持仓统计和验证机制
  - 优化策略文档和使用说明

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for full details.

You are free to use, modify, and distribute this project under the terms of the Apache License 2.0.
