# skills-research

這個專案用來管理 Claude Code 的 skills。

## 安裝的 Skills

### last30days

搜尋任何主題在過去 30 天內 Reddit、X、YouTube 和網頁上的討論，整理出社群正在討論的內容，並產生可直接使用的 prompts。

## 安裝

### 前置需求

- Python 3
- Node.js 22+
- OpenAI API Key

### 步驟

**1. Clone 此專案**

```bash
git clone <this-repo> ~/.claude/skills
```

或手動安裝單一 skill：

```bash
git clone https://github.com/mvanhorn/last30days-skill.git .claude/skills/last30days
```

**2. 設定環境變數**

複製範本並填入你的 API key：

```bash
cp .claude/settings.local.json.example .claude/settings.local.json
```

編輯 `.claude/settings.local.json`，將 `sk-...` 換成你的 OpenAI API key：

```json
{
  "env": {
    "OPENAI_API_KEY": "sk-..."
  }
}
```

## 使用方式

在 Claude Code 對話中輸入：

```
/last30days <主題>
/last30days <主題> for <工具>
```

### 範例

| 指令 | 說明 |
|------|------|
| `/last30days Claude Code skills` | 查詢 Claude Code skills 的最新討論 |
| `/last30days best AI tools` | 推薦最熱門 AI 工具清單 |
| `/last30days best image generation tools` | 推薦最佳圖片生成工具 |
| `/last30days iOS app mockups for Midjourney` | 查詢 Midjourney 製作 iOS mockup 的技巧並產生 prompt |
| `/last30days AI news` | 最近 30 天的 AI 新聞 |
| `/last30days --days=7 vibe coding` | 只查詢最近 7 天 |
| `/last30days --quick React trends` | 快速模式（資料較少但速度更快） |
| `/last30days --deep Cursor AI` | 深度模式（資料最完整） |

### 範例輸出：查詢熱門 AI 工具

**指令：** `/last30days best AI tools`

```
我將研究 best AI tools 的 Reddit、X 和網頁討論（最近 30 天）。

Parsed intent:
- TOPIC = AI tools
- TARGET_TOOL = unknown
- QUERY_TYPE = RECOMMENDATIONS

研究通常需要 2-8 分鐘。開始中...
```

**回傳結果範例：**

```
🏆 Most mentioned:

Cursor — 12x mentions
Use Case: AI-powered code editor, vibe coding 首選
Sources: @levelsio, @karpathy, r/ChatGPTCoding, r/LocalLLaMA

Claude Code — 9x mentions
Use Case: Terminal AI coding agent，支援 skills 擴充
Sources: @anthropy, r/ClaudeAI, Hacker News

Perplexity — 7x mentions
Use Case: AI 搜尋引擎，取代 Google
Sources: @aravindpu, r/artificial, r/MachineLearning

Notable mentions: Gemini Deep Research (5x), Grok 3 (4x), v0 (3x)

---
✅ All agents reported back!
├─ 🟠 Reddit: 28 threads │ 4,231 upvotes │ 892 comments
├─ 🔵 X: 41 posts │ 18,204 likes │ 3,017 reposts
├─ 🔴 YouTube: 6 videos │ 892,441 views │ 4 with transcripts
├─ 🌐 Web: 8 pages (supplementary)
└─ 🗣️ Top voices: @levelsio (8,412 likes), @karpathy │ r/LocalLLaMA, r/ChatGPTCoding
---
```

### 查詢類型

skill 會自動判斷查詢類型：

- **PROMPTING** — 「X prompts」、「prompting for X」→ 產生可貼上的 prompt
- **RECOMMENDATIONS** — 「best X」、「top X」→ 列出具體推薦清單
- **NEWS** — 「X news」、「latest on X」→ 最新動態與事件
- **GENERAL** — 其他 → 廣泛了解該主題

### 選項

| 選項 | 說明 |
|------|------|
| `--days=N` | 查詢最近 N 天（預設 30） |
| `--quick` | 快速模式，每個來源 8-12 筆 |
| `--deep` | 深度模式，Reddit 50-70 筆、X 40-60 筆 |


## 參考

[last30days-skill](https://github.com/mvanhorn/last30days-skill)
