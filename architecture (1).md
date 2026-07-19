# 系统架构图

将以下 Mermaid 代码粘贴到 [Mermaid Live Editor](https://mermaid.live) 可导出为 PNG 图片。

```mermaid
graph TB
    subgraph Data[数据层]
        A1[搜索趋势 <br/>百度指数]
        A2[短视频热度]
        A3[交通迁徙 <br/>高德迁徙]
        A4[天气数据]
        A5[节假日信息]
    end
    subgraph Process[处理层]
        B[特征工程]
        C[时间序列预测 <br/>Prophet]
        D[运营优先级评分 <br/>热度 x 供给能力]
    end
    subgraph Output[输出层]
        E[prediction.json]
    end
    subgraph Frontend[展示层]
        F[AI 运营驾驶舱]
        F1[潜力城市 Top10]
        F2[热度趋势图]
        F3[AI 判断依据]
        F4[运营建议]
    end
    A1 --> B; A2 --> B; A3 --> B; A4 --> B; A5 --> B
    B --> C; C --> D; D --> E; E --> F
    F --> F1; F --> F2; F --> F3; F --> F4
```

## 架构说明

本系统定位为"面向去哪儿运营团队的潜力城市预警与决策支持平台"，而非单纯的预测模型。预测仅作为系统的一个模块，最终交付的是可操作的运营预警清单与资源配置建议。系统分为四层：数据层（公开数据采集）、处理层（特征工程与 Prophet 预测）、输出层（prediction.json）和展示层（运营驾驶舱）。