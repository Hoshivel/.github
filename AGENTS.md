<!-- hoshivel:agent-rules v1 -> https://github.com/Hoshivel/workspace -->

# AGENTS.md — .github

> 共通流程以 [workspace](https://github.com/Hoshivel/workspace) 的 `AGENTS.md`
> 為準；本檔只列本倉庫規則。

## 0. 開工前

1. 讀 `../workspace/focus.md` 與 `../workspace/AGENTS.md`；缺少時先
   `git clone https://github.com/Hoshivel/workspace.git ../workspace`，
   取不到就停止並說明。
2. 待辦與日誌在 `workspace/todo/.github/`、`workspace/logs/.github/`；
   不得在本倉庫另建副本。

## 1. 入場閱讀順序

1. `agents/`：本倉庫提供給 GitHub／VS Code 的可重用代理定義。
2. 要修改的 `agents/*.agent.md`：先讀 YAML frontmatter 的工具範圍、觸發方式與
   目標，再讀正文中的工作限制與編輯流程。

## 2. 驗證

改動後執行；通過後再更新該事項的工作區狀態：

- `python ../workspace/tools/check-agent-rules.py --root .. --verbose`：確認本倉庫與
  所有可見 sibling 倉庫都有入口，且沒有把共通工作狀態放回產品倉庫。
- `git diff --check`：確認 Markdown 與 frontmatter 沒有空白錯誤。

## 3. 這個倉庫的特殊規則

- 每個代理檔必須保留 YAML frontmatter 與 Markdown 正文；`tools` 只列出該代理實際
  允許使用的工具。
- 代理正文必須明確寫出目標範圍、不可使用的能力，以及完成前的重讀／驗證步驟；
  不得把 workspace 的跨倉庫流程複製進來。
- `agents/story-edit.agent.md` 的窄工具面是有意的安全邊界：故事編輯只能搜尋、讀取、
  編輯與提問，不得執行命令、測試、建置、瀏覽網路或呼叫子代理。
- 文件沿用各代理現有語言與格式；工作狀態只記在 workspace。
