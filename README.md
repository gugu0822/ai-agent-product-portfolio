# ai-agent-product-portfolio
AI Agent product portfolio | LLM workflow design &amp; demo scripts
AI 应用开发作品集
三个从 0 到 1 独立完成的自动化应用：覆盖语音外呼、内容营销、数据采集三个业务场景。
强调工程落地能力：方案设计、多级降级策略、配置外部化、自动化测试与异常处理。

📞 项目一：面试预约外呼机器人（interview-reserve-agent）
一句话定位：用 AI 语音机器人自动批量拨打候选人电话，完成面试预约全流程。

核心能力

基于阿里云智能外呼 + 大模型多轮对话：确认身份 → 确认意向 → 协商面试时间 → 自动避峰
智能时段管理：工作日时段自动生成、"人工已约时段"自动排除、串行拨打防止重复预约
通话结果自动分类（已预约 / 号码错误 / 无意向 / 需HR协调 / 未接通），一键导出 Excel 汇总报表 + 分城市面试时间表
敏感配置（实例ID、脚本ID、主叫号码）全部环境变量化，凭证本地存放，可安全开源
技术栈：Python · 阿里云 OutboundBot SDK · 大模型对话 · openpyxl · JSON 数据驱动

质量保障：输入校验器 16 项 + 核心逻辑模拟测试 19 项全部通过（含边界值、注入、重复数据用例）。

📧 项目二：邮件营销自动化智能体（email-marketing-agent）
一句话定位：内容写好后一键生成多业务线 HTML 邮件并自动推送企业微信群。

核心能力

内容与渲染分离：只改 email_data.py 数据文件，引擎自动渲染为响应式 HTML 邮件 + Campaign 投放建议
多业务线并行：一套引擎支持多条内容线（少儿中文 / IB 中文 / IGCSE 中文），按品牌自动路由到对应企微群
邮件母版工程化：A/B 标题、预览文字、CTA、互动钩子、UTM 跟踪参数全部可配置
配置外部化：企微 webhook key 通过环境变量 / 外部配置文件读取，绝不入库、可安全开源
技术栈：Python · HTML 模板引擎（逻辑与展示分离）· 企业微信 Webhook API · 文件生成与自动发送

运行方式：generate_emails.py 生成 → send_to_wechat.py --brand <业务线> 自动匹配群并推送，实测一次生成 3 份 HTML + 3 份 Campaign。

🕷️ 项目三：海外社区内容采集与分析工具（forum-scraper）
一句话定位：多策略爬取海外论坛/社区帖子，产出结构化线索数据，用于精准获客与市场调研。

核心能力

四级策略自动降级：直接爬取（requests+BS4）→ DuckDuckGo 搜索 → WebFetch → 浏览器自动化（JS渲染/登录页），被屏蔽也能拿到数据
工程化解析：适配 AJAX API 分页、搜索接口、动态列表三种站点结构；3 个真实海外站点已跑通
数据管线：URL/标题去重 → 时间过滤（默认近3个月）→ 关键字相关性过滤 → CSV（utf-8-sig，Excel 直开）
合规设计：只采集公开信息，输出字段不含联系方式等隐私；自带限速与随机 UA 防反爬
技术栈：Python · requests · BeautifulSoup · DuckDuckGo 搜索 · 浏览器自动化 · csv 数据管线

🛠️ 技术栈汇总
方向	技术
语言	Python 3
网络/采集	requests · BeautifulSoup · WebFetch · 浏览器自动化
云服务	阿里云智能外呼（OutboundBot SDK）· 企业微信 Webhook API
数据处理	openpyxl（Excel 报表）· csv · JSON · utf-8-sig 兼容
工程实践	配置环境变量化 · 多级降级 · 自动化测试 · 数据驱动
✉️ 联系方式
邮件：3457357623@qq.com
