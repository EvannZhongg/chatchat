# Langchain-Chatchat 目录结构说明

本文档详细说明了 Langchain-Chatchat 项目的目录结构及其功能。

```
Langchain-Chatchat/
├── basic_settings.yaml          # 基础配置文件，包含项目基本设置
├── kb_settings.yaml             # 知识库相关配置，如向量数据库、检索参数等
├── model_settings.yaml          # 模型配置，定义LLM和Embedding模型的参数
├── prompt_settings.yaml         # 提示词配置，包含各类对话和检索的提示词模板
├── tool_settings.yaml           # 工具配置，定义Agent工具的参数和设置
├── poetry.toml                  # Poetry依赖管理配置文件
├── pyproject.toml               # Python项目配置文件，定义项目元数据和依赖
├── README.md                    # 项目说明文档（中文）
├── README_en.md                 # 项目说明文档（英文）
├── LICENSE                      # 项目许可证文件
├── release.py                   # 版本发布脚本
│
├── data/                        # 数据目录，存放运行时生成的数据
│   ├── knowledge_base/          # 知识库数据存储
│   │   ├── info.db             # 知识库元数据数据库（SQLite）
│   │   ├── protein/            # 蛋白相关的知识库
│   │   │   ├── content/        # 原始文档内容存储
│   │   │   └── vector_store/   # 向量数据库存储（用于相似度检索）
│   │   └── samples/            # 示例知识库，包含测试文档
│   ├── logs/                   # 日志文件目录
│   │   ├── chatchat.log        # 主应用日志
│   │   ├── run_api_server_*/   # API服务器运行日志（按时间戳命名）
│   │   ├── run_webui_*/        # WebUI运行日志（按时间戳命名）
│   │   └── start_main_server_*/ # 主服务器启动日志（按时间戳命名）
│   ├── media/                  # 媒体文件目录
│   │   ├── audio/              # 音频文件
│   │   ├── image/              # 图片文件
│   │   └── video/              # 视频文件
│   ├── nltk_data/              # NLTK自然语言处理工具包数据
│   └── temp/                   # 临时文件目录
│       └── openai_files/       # OpenAI文件API相关的临时文件
│
├── docker/                      # Docker部署相关文件
│   ├── docker-compose.yaml     # Docker Compose编排文件
│   ├── Dockerfile              # Docker镜像构建文件
│   └── data.tar.gz             # 数据压缩包
│
├── docs/                        # 项目文档目录
│   ├── contributing/           # 贡献指南和开发文档
│   │   ├── agent.md           # Agent功能开发指南
│   │   ├── api.md             # API开发文档
│   │   ├── code.md            # 代码规范
│   │   ├── README_dev.md      # 开发环境搭建指南
│   │   ├── README.md          # 贡献者指南主文档
│   │   ├── repo_structure.md  # 仓库结构说明
│   │   └── settings.md        # 配置说明文档
│   ├── img/                    # 文档图片资源
│   │   ├── chatchat_icon_*.png # 项目图标
│   │   ├── langchain*.png      # LangChain相关图片
│   │   ├── logo-*.png          # 项目Logo
│   │   ├── *.jpg               # 二维码等图片
│   │   └── partners/           # 合作伙伴Logo
│   └── install/                # 安装相关文档
│       ├── README_docker.md    # Docker安装指南
│       ├── README_text2sql.md  # Text2SQL功能安装说明
│       ├── README_xinference.md # Xinference部署指南（中文）
│       └── README_xinference_en.md # Xinference部署指南（英文）
│
├── libs/                        # 核心库目录
│   ├── chatchat-server/        # 主服务器库
│   │   ├── chatchat/           # 核心应用代码
│   │   │   ├── __init__.py
│   │   │   ├── cli.py          # 命令行接口
│   │   │   ├── settings.py     # 设置管理
│   │   │   ├── startup.py      # 启动脚本
│   │   │   ├── utils.py        # 工具函数
│   │   │   ├── webui.py        # WebUI入口
│   │   │   ├── init_database.py # 数据库初始化脚本
│   │   │   ├── pydantic_settings_file.py # Pydantic配置管理
│   │   │   │
│   │   │   ├── data/           # 应用数据目录
│   │   │   │   ├── knowledge_base/ # 知识库示例数据
│   │   │   │   └── nltk_data/  # NLTK数据
│   │   │   │
│   │   │   ├── img/            # 应用图片资源
│   │   │   │
│   │   │   ├── server/         # 服务器核心代码
│   │   │   │   ├── __init__.py
│   │   │   │   ├── api_allinone_stale.py # 旧版API集成（已弃用）
│   │   │   │   ├── llm_api_shutdown.py   # LLM API关闭处理
│   │   │   │   ├── llm_api_stale.py      # 旧版LLM API（已弃用）
│   │   │   │   ├── webui_allinone_stale.py # 旧版WebUI（已弃用）
│   │   │   │   ├── utils.py    # 服务器工具函数
│   │   │   │   ├── localai_embeddings.py # LocalAI嵌入模型
│   │   │   │   ├── pydantic_v1.py        # Pydantic v1兼容
│   │   │   │   ├── pydantic_v2.py        # Pydantic v2兼容
│   │   │   │   │
│   │   │   │   ├── agent/      # Agent相关功能
│   │   │   │   │   └── tools_factory/ # 工具工厂
│   │   │   │   │       ├── __init__.py
│   │   │   │   │       ├── tools_registry.py # 工具注册表
│   │   │   │   │       ├── calculate.py      # 计算器工具
│   │   │   │   │       ├── search_internet.py # 网络搜索工具
│   │   │   │   │       ├── search_local_knowledgebase.py # 本地知识库搜索
│   │   │   │   │       ├── search_youtube.py # YouTube搜索
│   │   │   │   │       ├── text2image.py     # 文本生成图片
│   │   │   │   │       ├── text2promql.py    # PromQL查询工具
│   │   │   │   │       ├── text2sql.py       # SQL生成工具
│   │   │   │   │       ├── url_reader.py     # URL内容读取
│   │   │   │   │       ├── arxiv.py          # ArXiv论文搜索
│   │   │   │   │       ├── wikipedia_search.py # 维基百科搜索
│   │   │   │   │       ├── wolfram.py        # Wolfram Alpha计算
│   │   │   │   │       ├── weather_check.py  # 天气查询
│   │   │   │   │       ├── amap_weather.py   # 高德天气API
│   │   │   │   │       ├── amap_poi_search.py # 高德POI搜索
│   │   │   │   │       └── shell.py          # Shell命令执行
│   │   │   │   │
│   │   │   │   ├── agents_registry/ # Agent注册管理
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   └── agents_registry.py # Agent注册表
│   │   │   │   │
│   │   │   │   ├── api_server/ # FastAPI服务器
│   │   │   │   │   ├── server_app.py    # FastAPI应用主文件
│   │   │   │   │   ├── api_schemas.py   # API数据模型定义
│   │   │   │   │   ├── chat_routes.py   # 聊天相关路由
│   │   │   │   │   ├── kb_routes.py     # 知识库相关路由
│   │   │   │   │   ├── tool_routes.py   # 工具相关路由
│   │   │   │   │   ├── mcp_routes.py    # MCP协议路由
│   │   │   │   │   ├── openai_routes.py # OpenAI兼容API路由
│   │   │   │   │   ├── server_routes.py # 服务器管理路由
│   │   │   │   │   └── static/          # 静态资源
│   │   │   │   │       ├── favicon.png  # 网站图标
│   │   │   │   │       ├── swagger-ui.* # Swagger UI文件（API文档）
│   │   │   │   │       └── redoc.standalone.js # ReDoc文档工具
│   │   │   │   │
│   │   │   │   ├── chat/       # 聊天功能模块
│   │   │   │   │   ├── chat.py          # 基础聊天实现
│   │   │   │   │   ├── completion.py    # 文本补全功能
│   │   │   │   │   ├── feedback.py      # 反馈处理
│   │   │   │   │   ├── file_chat.py     # 文件聊天功能
│   │   │   │   │   ├── kb_chat.py       # 知识库聊天功能
│   │   │   │   │   ├── human_message_event.py # 用户消息事件处理
│   │   │   │   │   └── utils.py         # 聊天工具函数
│   │   │   │   │
│   │   │   │   ├── constant/   # 常量定义
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   └── response_code.py # HTTP响应码定义
│   │   │   │   │
│   │   │   │   ├── db/         # 数据库相关
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── base.py          # 数据库基础类
│   │   │   │   │   ├── session.py       # 数据库会话管理
│   │   │   │   │   ├── models/          # 数据模型（ORM）
│   │   │   │   │   │   ├── __init__.py
│   │   │   │   │   │   ├── base.py              # 基础模型类
│   │   │   │   │   │   ├── conversation_model.py # 对话模型
│   │   │   │   │   │   ├── message_model.py     # 消息模型
│   │   │   │   │   │   ├── knowledge_base_model.py # 知识库模型
│   │   │   │   │   │   ├── knowledge_file_model.py # 知识库文件模型
│   │   │   │   │   │   ├── knowledge_metadata_model.py # 知识库元数据模型
│   │   │   │   │   │   ├── human_message_event_model.py # 用户消息事件模型
│   │   │   │   │   │   └── mcp_connection_model.py # MCP连接模型
│   │   │   │   │   └── repository/      # 数据访问层（Repository模式）
│   │   │   │   │       ├── __init__.py
│   │   │   │   │       ├── conversation_repository.py # 对话数据访问
│   │   │   │   │       ├── message_repository.py      # 消息数据访问
│   │   │   │   │       ├── knowledge_base_repository.py # 知识库数据访问
│   │   │   │   │       ├── knowledge_file_repository.py # 知识库文件数据访问
│   │   │   │   │       ├── knowledge_metadata_repository.py # 元数据数据访问
│   │   │   │   │       ├── human_message_event_repository.py # 事件数据访问
│   │   │   │   │       └── mcp_connection_repository.py # MCP连接数据访问
│   │   │   │   │
│   │   │   │   ├── file_rag/   # 文件RAG（检索增强生成）模块
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── utils.py         # RAG工具函数
│   │   │   │   │   ├── document_loaders/ # 文档加载器
│   │   │   │   │   │   ├── __init__.py
│   │   │   │   │   │   ├── mypdfloader.py    # PDF加载器
│   │   │   │   │   │   ├── mydocloader.py    # DOC/DOCX加载器
│   │   │   │   │   │   ├── mypptloader.py    # PPT加载器
│   │   │   │   │   │   ├── myimgloader.py    # 图片加载器
│   │   │   │   │   │   ├── FilteredCSVloader.py # CSV加载器（带过滤）
│   │   │   │   │   │   └── ocr.py             # OCR文字识别
│   │   │   │   │   ├── text_splitter/    # 文本分割器
│   │   │   │   │   │   ├── __init__.py
│   │   │   │   │   │   ├── chinese_recursive_text_splitter.py # 中文递归分割
│   │   │   │   │   │   ├── chinese_text_splitter.py # 中文文本分割
│   │   │   │   │   │   ├── ali_text_splitter.py    # 阿里云文本分割
│   │   │   │   │   │   └── zh_title_enhance.py     # 中文标题增强
│   │   │   │   │   └── retrievers/       # 检索器
│   │   │   │   │       ├── __init__.py
│   │   │   │   │       ├── base.py              # 检索器基类
│   │   │   │   │       ├── vectorstore.py       # 向量检索器
│   │   │   │   │       ├── milvus_vectorstore.py # Milvus向量检索
│   │   │   │   │       └── ensemble.py          # 集成检索器（混合检索）
│   │   │   │   │
│   │   │   │   ├── knowledge_base/ # 知识库管理模块
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── kb_api.py        # 知识库API接口
│   │   │   │   │   ├── kb_doc_api.py    # 知识库文档API
│   │   │   │   │   ├── kb_summary_api.py # 知识库摘要API
│   │   │   │   │   ├── migrate.py       # 数据迁移脚本
│   │   │   │   │   ├── utils.py         # 知识库工具函数
│   │   │   │   │   ├── model/           # 知识库数据模型
│   │   │   │   │   │   └── kb_document_model.py # 文档模型
│   │   │   │   │   ├── kb_service/      # 知识库服务实现
│   │   │   │   │   │   ├── __init__.py
│   │   │   │   │   │   ├── base.py              # 知识库服务基类
│   │   │   │   │   │   ├── default_kb_service.py # 默认服务
│   │   │   │   │   │   ├── faiss_kb_service.py  # FAISS向量数据库服务
│   │   │   │   │   │   ├── milvus_kb_service.py # Milvus向量数据库服务
│   │   │   │   │   │   ├── chromadb_kb_service.py # ChromaDB服务
│   │   │   │   │   │   ├── pg_kb_service.py     # PostgreSQL向量服务
│   │   │   │   │   │   ├── es_kb_service.py     # Elasticsearch服务
│   │   │   │   │   │   ├── relyt_kb_service.py  # Relyt向量数据库服务
│   │   │   │   │   │   └── zilliz_kb_service.py # Zilliz Cloud服务
│   │   │   │   │   ├── kb_cache/        # 知识库缓存
│   │   │   │   │   │   ├── base.py      # 缓存基类
│   │   │   │   │   │   └── faiss_cache.py # FAISS缓存实现
│   │   │   │   │   └── kb_summary/      # 知识库摘要功能
│   │   │   │   │       ├── __init__.py
│   │   │   │   │       ├── base.py      # 摘要基类
│   │   │   │   │       └── summary_chunk.py # 分块摘要实现
│   │   │   │   │
│   │   │   │   ├── reranker/   # 重排序模块
│   │   │   │   │   └── reranker.py # 检索结果重排序
│   │   │   │   │
│   │   │   │   └── types/      # 类型定义
│   │   │   │       ├── __init__.py
│   │   │   │       └── server/ # 服务器类型
│   │   │   │           ├── __init__.py
│   │   │   │           └── response/    # 响应类型定义
│   │   │   │
│   │   │   └── webui_pages/    # WebUI页面
│   │   │       ├── __init__.py
│   │   │       ├── utils.py    # WebUI工具函数
│   │   │       ├── kb_chat.py  # 知识库聊天页面
│   │   │       ├── dialogue/   # 对话页面
│   │   │       │   ├── __init__.py
│   │   │       │   ├── dialogue.py # 对话页面实现
│   │   │       │   └── utils.py    # 对话工具函数
│   │   │       ├── knowledge_base/ # 知识库管理页面
│   │   │       │   ├── __init__.py
│   │   │       │   └── knowledge_base.py # 知识库管理实现
│   │   │       ├── model_config/ # 模型配置页面
│   │   │       │   ├── __init__.py
│   │   │       │   └── model_config.py # 模型配置实现
│   │   │       └── mcp/        # MCP协议页面
│   │   │           ├── __init__.py
│   │   │           └── dialogue.py # MCP对话页面
│   │   │
│   │   └── langchain_chatchat/ # LangChain集成代码
│   │       ├── __init__.py
│   │       ├── agents/         # Agent实现
│   │       │   ├── __init__.py
│   │       │   ├── all_tools_agent.py # 全工具Agent
│   │       │   ├── react/      # ReAct Agent
│   │       │   │   └── create_prompt_template.py # 提示词模板创建
│   │       │   ├── structured_chat/ # 结构化聊天Agent
│   │       │   │   ├── __init__.py
│   │       │   │   ├── structured_chat_agent.py # 结构化聊天Agent基础
│   │       │   │   ├── qwen_agent.py    # Qwen模型Agent
│   │       │   │   ├── glm3_agent.py    # GLM3模型Agent
│   │       │   │   ├── platform_knowledge_bind.py # 平台知识绑定
│   │       │   │   └── platform_tools_bind.py # 平台工具绑定
│   │       │   ├── format_scratchpad/ # 格式化暂存
│   │       │   │   └── all_tools.py
│   │       │   ├── output_parsers/ # 输出解析器
│   │       │   │   ├── __init__.py
│   │       │   │   ├── structured_chat_output_parsers.py # 结构化输出解析
│   │       │   │   ├── qwen_output_parsers.py # Qwen输出解析
│   │       │   │   ├── glm3_output_parsers.py # GLM3输出解析
│   │       │   │   ├── platform_knowledge_output_parsers.py # 平台知识输出解析
│   │       │   │   ├── platform_tools.py # 平台工具
│   │       │   │   └── tools_output/ # 工具输出处理
│   │       │   │       ├── __init__.py
│   │       │   │       ├── base.py
│   │       │   │       ├── tools.py
│   │       │   │       ├── function.py
│   │       │   │       ├── code_interpreter.py # 代码解释器输出
│   │       │   │       ├── drawing_tool.py # 绘图工具输出
│   │       │   │       └── web_browser.py # 浏览器工具输出
│   │       │   └── platform_tools/ # 平台工具
│   │       │       ├── __init__.py
│   │       │       ├── base.py
│   │       │       └── schema.py
│   │       │
│   │       ├── agent_toolkits/ # Agent工具包
│   │       │   ├── __init__.py
│   │       │   ├── all_tools/  # 所有工具集成
│   │       │   │   ├── __init__.py
│   │       │   │   ├── registry.py # 工具注册表
│   │       │   │   ├── tool.py     # 工具基类
│   │       │   │   ├── struct_type.py # 结构化类型
│   │       │   │   ├── code_interpreter_tool.py # 代码解释器工具
│   │       │   │   ├── drawing_tool.py # 绘图工具
│   │       │   │   └── web_browser_tool.py # 浏览器工具
│   │       │   └── mcp_kit/    # MCP工具包
│   │       │       ├── client.py # MCP客户端
│   │       │       ├── prompts.py # MCP提示词
│   │       │       └── tools.py # MCP工具
│   │       │
│   │       ├── callbacks/      # 回调函数
│   │       │   ├── __init__.py
│   │       │   ├── agent_callback_handler.py # Agent回调处理器
│   │       │   └── core/       # 核心回调
│   │       │       └── protocol.py # 回调协议定义
│   │       │
│   │       ├── chat_models/    # 聊天模型
│   │       │   ├── __init__.py
│   │       │   ├── base.py     # 聊天模型基类
│   │       │   └── platform_tools_message.py # 平台工具消息
│   │       │
│   │       ├── embeddings/     # 嵌入模型
│   │       │   ├── __init__.py
│   │       │   └── zhipuai.py  # 智谱AI嵌入模型
│   │       │
│   │       └── utils/          # 工具函数
│   │           ├── __init__.py
│   │           ├── history.py  # 历史记录处理
│   │           └── try_parse_json_object.py # JSON解析工具
│   │
│   ├── Makefile                # Make构建文件
│   ├── poetry.toml             # Poetry配置
│   ├── pyproject.toml          # Python项目配置
│   ├── README.md               # 库说明文档
│   ├── README_en.md            # 库说明文档（英文）
│   ├── scripts/                # 构建和部署脚本
│   └── tests/                  # 测试文件
│
│   └── python-sdk/             # Python SDK（客户端库）
│       ├── open_chatcaht/      # SDK主要代码
│       ├── poetry.toml         # Poetry配置
│       ├── pyproject.toml      # Python项目配置
│       └── tests/              # SDK测试
│
├── markdown_docs/              # Markdown格式的功能文档
│   ├── document_loaders/       # 文档加载器文档
│   │   ├── FilteredCSVloader.md
│   │   ├── mydocloader.md
│   │   ├── myimgloader.md
│   │   ├── mypdfloader.md
│   │   ├── mypptloader.md
│   │   └── ocr.md
│   ├── embeddings/             # 嵌入模型文档
│   │   └── add_embedding_keywords.md
│   ├── text_splitter/          # 文本分割器文档
│   │   ├── ali_text_splitter.md
│   │   ├── chinese_recursive_text_splitter.md
│   │   ├── chinese_text_splitter.md
│   │   └── zh_title_enhance.md
│   ├── server/                 # 服务器文档
│   ├── webui_pages/            # WebUI页面文档
│   │   ├── dialogue/           # 对话页面文档
│   │   ├── knowledge_base/     # 知识库页面文档
│   │   ├── model_config/       # 模型配置页面文档
│   │   └── utils.md            # WebUI工具文档
│   └── release.md              # 版本发布说明
│   └── startup.md              # 启动说明文档
│
└── tools/                      # 工具脚本目录
    ├── autodl_start_script/    # AutoDL启动脚本
    │   ├── download_model.sh   # 模型下载脚本
    │   ├── model_registrations.sh # 模型注册脚本
    │   ├── model_registrations_emb.sh # 嵌入模型注册脚本
    │   ├── start_chatchat.sh   # ChatChat启动脚本
    │   ├── start_models.sh     # 模型启动脚本
    │   ├── start_models_emb.sh # 嵌入模型启动脚本
    │   ├── start_xinference.sh # Xinference启动脚本
    │   └── startup.sh          # 总启动脚本
    └── model_loaders/          # 模型加载器工具
        ├── basic_settings.yaml # 基础设置
        ├── kb_settings.yaml    # 知识库设置
        ├── model_settings.yaml # 模型设置
        ├── prompt_settings.yaml # 提示词设置
        ├── tool_settings.yaml  # 工具设置
        ├── xinference_manager.py # Xinference管理器
        └── data/               # 工具数据目录
            ├── knowledge_base/ # 知识库数据
            ├── logs/           # 日志
            ├── media/          # 媒体文件
            ├── nltk_data/      # NLTK数据
            └── temp/           # 临时文件
```

## 核心目录说明

### 1. `/libs/chatchat-server/chatchat/` - 核心应用代码
这是项目的核心目录，包含所有主要的应用逻辑：
- **server/**: 服务器核心功能，包括API、聊天、知识库等
- **webui_pages/**: Streamlit WebUI界面代码
- **data/**: 应用数据示例

### 2. `/libs/chatchat-server/langchain_chatchat/` - LangChain集成
包含与LangChain框架的集成代码：
- **agents/**: Agent实现，支持多种Agent模式
- **agent_toolkits/**: Agent工具包
- **callbacks/**: 回调处理器
- **chat_models/**: 聊天模型封装
- **embeddings/**: 嵌入模型

### 3. `/data/` - 运行时数据
存储应用运行时的所有数据：
- 知识库文件和向量索引
- 日志文件
- 媒体文件
- 临时文件

### 4. `/docs/` - 项目文档
包含完整的项目文档，包括：
- 安装指南
- 开发指南
- API文档
- 贡献指南

### 5. `/tools/` - 工具脚本
包含各种部署和启动脚本，方便在不同环境中部署项目。

## 主要功能模块

1. **API服务器** (`server/api_server/`): 基于FastAPI的RESTful API
2. **知识库管理** (`server/knowledge_base/`): 知识库的增删改查和向量化
3. **Agent系统** (`server/agent/`, `langchain_chatchat/agents/`): Agent和工具调用
4. **文件RAG** (`server/file_rag/`): 文档加载、分割和检索
5. **WebUI** (`webui_pages/`): Streamlit用户界面
6. **数据库** (`server/db/`): 数据持久化层

## 配置文件说明

- `basic_settings.yaml`: 基础配置
- `model_settings.yaml`: LLM和Embedding模型配置
- `kb_settings.yaml`: 知识库和向量数据库配置
- `prompt_settings.yaml`: 提示词模板配置
- `tool_settings.yaml`: Agent工具配置

每个配置文件都定义了对应模块的参数，修改这些文件可以调整系统的行为。

