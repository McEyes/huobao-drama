# Tasks

- [x] Task 1: 扩展前端 AI 服务提供商配置
  - [x] SubTask 1.1: 在 `web/src/components/common/AIConfigDialog.vue` 中扩展 `providerConfigs` 对象，增加 Doubao (豆包), Qwen (通义千问), Kimi (Moonshot) 的配置信息（包括模型列表和名称）。
  - [x] SubTask 1.2: 更新 `handleProviderChange` 方法，添加新厂商的默认 Base URL 设置逻辑。
  - [x] SubTask 1.3: 更新 `fullEndpointExample` 计算属性，确保新厂商的 API 端点示例正确显示。
  - [x] SubTask 1.4: 更新 `generateConfigName` 方法，添加新厂商的中文名称映射（如 `doubao` -> `豆包`）。

- [x] Task 2: 扩展后端 AI 服务提供商支持
  - [x] SubTask 2.1: 在 `application/services/ai_service.go` 的 `CreateConfig` 方法中，增加对 `doubao`, `qwen`, `kimi` 等新厂商的 `Endpoint` 自动配置逻辑。
  - [x] SubTask 2.2: 在 `application/services/ai_service.go` 的 `UpdateConfig` 方法中，同步增加对新厂商的 `Endpoint` 更新逻辑。
  - [x] SubTask 2.3: 检查并确保 `GetAIClient` 方法能正确处理新厂商的配置（默认为 OpenAI 兼容模式）。

- [x] Task 3: 验证新厂商配置
  - [x] SubTask 3.1: 启动应用，验证在 AI 配置弹窗中是否可以看到新添加的厂商。
  - [x] SubTask 3.2: 验证选择新厂商时，默认 Base URL 和模型列表是否正确加载。
  - [x] SubTask 3.3: 尝试保存配置，验证后端是否正确接收并存储了配置信息。
