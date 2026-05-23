# Chat To Angst Fiction

把聊天记录、私信、微信/QQ 导出或关系笔记，改写成克制、证据驱动的中文虐文。

这个 skill 的核心不是“加戏”，而是反过来：每一句叙事都要能回到聊天记录里的某条消息、某个时间戳、某种可观察模式。它适合把一段真实关系整理成 BE 短篇、第一人称独白、遗憾文学、聊天体虐文，或更适合发布的匿名化情绪文本。

它也是一个只供自己看的项目：只有当事人本人会被这些证据和句子真正触动；之所以注定是 BE，是因为 he 不可能来用这个项目。

## What It Does

- 读取聊天记录、截图转写稿、DM、微信/QQ 导出或关系笔记。
- 提取关系结构、冲突、转折点、伤人的原话和结束情绪。
- 用证据规则约束写作，避免凭空编造外貌、场景和对方心理。
- 自动提示隐私保护：真实姓名、账号、电话、地址、学校/公司等需要匿名化。
- 可选用 `scripts/generate_docx.py` 把 Markdown 文稿转成适合中文阅读的 `.docx`。

## Evidence Standard

写作时按证据等级使用材料：

- 直接引用：聊天原文、时间戳、发送者。
- 可观察模式：回复变短、间隔变长、称呼变化、主动次数变化。
- 统计事实：消息数量、时间跨度、发送比例。
- 谨慎推断：只能推断叙述方可能的感受，并用“也许 / 大概 / 可能”标记。
- 真实物件：聊天中明确出现过的礼物、链接、图片、语音、撤回等。

禁止编造没有证据的天气、灯光、衣服、动作、对方内心、未来重逢等戏剧细节。

## Install

Clone this repository into your skills directory:

```powershell
git clone https://github.com/<your-name>/chat-to-angst-fiction.git "$env:USERPROFILE\.codex\skills\chat-to-angst-fiction"
```

For Claude-style skills, clone it into:

```powershell
git clone https://github.com/<your-name>/chat-to-angst-fiction.git "$env:USERPROFILE\.claude\skills\chat-to-angst-fiction"
```

## Example Prompt

```text
Use $chat-to-angst-fiction to turn this chat log into a restrained Chinese BE short story.
Protect privacy, preserve the core relationship dynamics, and make every emotional claim traceable to a timestamped message.
```

## Files

- `SKILL.md` - the skill instructions.
- `references/evidence-rules.md` - detailed evidence rules for chat-based fiction.
- `scripts/generate_docx.py` - Markdown to DOCX converter with Chinese font defaults.
- `agents/openai.yaml` - UI metadata for Codex-style skill lists.

## Privacy

Do not commit real chat exports, screenshots, names, QQ/WeChat IDs, phone numbers, addresses, school/company names, private links, or evidence maps derived from a real relationship. Keep private evidence outside the repository.
