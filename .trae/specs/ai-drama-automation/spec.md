# AI服务提供商扩展 Spec

## Why
为了提供更多样化的AI模型选择，满足不同用户对成本、性能和特定能力的需求，需要扩展系统支持的AI服务提供商。

## What Changes
### Frontend
- **修改 `web/src/components/common/AIConfigDialog.vue`**:
  - 扩展 `providerConfigs` 配置对象，增加以下厂商：
    - **豆包 (Doubao)**: 文本、图像、视频生成
    - **通义千问 (Qwen)**: 文本、图像生成
    - **Kimi (Moonshot)**: 文本生成
  - 更新 `handleProviderChange` 方法，为新厂商提供默认的 Base URL。
  - 更新 `fullEndpointExample` 计算属性，显示新厂商的 API 端点示例。
  - 更新 `generateConfigName` 方法，支持新厂商的中文名称映射。

### Backend
- **修改 `application/services/ai_service.go`**:
  - 在 `CreateConfig` 和 `UpdateConfig` 方法中，增加对新厂商 (`doubao`, `qwen`, `kimi`) 的默认 Endpoint 处理逻辑。
  - 确保 `GetAIClient` 能正确处理这些厂商的配置（通常兼容 OpenAI 协议）。

## Impact
- **Affected specs**: AI Configuration
- **Affected code**: 
  - `web/src/components/common/AIConfigDialog.vue`
  - `application/services/ai_service.go`

## ADDED Requirements
### Requirement: AI服务提供商扩展
系统应支持以下AI服务提供商的配置和使用：

#### 1. 豆包 (Doubao)
- **Service Types**: Text, Image, Video
- **Provider ID**: `doubao`
- **Default Base URL**: `https://ark.cn-beijing.volces.com/api/v3` (Text/Image)
- **Models**: `doubao-pro-4k`, `doubao-lite-4k`, `doubao-seedream` (Image), `doubao-seedance` (Video)

#### 2. 通义千问 (Qwen)
- **Service Types**: Text, Image
- **Provider ID**: `qwen`
- **Default Base URL**: `https://dashscope.aliyuncs.com/compatible-mode/v1`
- **Models**: `qwen-turbo`, `qwen-plus`, `qwen-max`, `wanx-v1` (Image)

#### 3. Kimi (Moonshot)
- **Service Types**: Text
- **Provider ID**: `kimi`
- **Default Base URL**: `https://api.moonshot.cn/v1`
- **Models**: `moonshot-v1-8k`, `moonshot-v1-32k`, `moonshot-v1-128k`
