# 解决方案

本项目是一个 Amazon Bedrock 以及其他大语言模型或应用的转发工具，他可以管理虚拟 API Key，记录聊天记录，并管理成本。

它与任何可以定义 Host 和 API 密钥的 OpenAI 客户端兼容。

## 二级目录的二级标题

您可以自定义模型价格. [Bedrock 模型的基准价格可以参考官网](https://aws.amazon.com/bedrock/pricing).

!!! warning

    这个项目的成本计算不能作为 AWS 的计费依据。实际支出请参考 AWS 账单。

### 模型管理

模型及其参数可以从后端定义。参见[创建模型](../user-manual/management.md#models)。

定义完成之后，模型可以绑定到组或者 API Key。
