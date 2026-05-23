---
name: chat-to-angst-fiction
description: Transform chat logs, message screenshots/transcripts, DMs, WeChat/QQ conversations, or relationship notes into Chinese angst fiction. Use when the user asks to turn 聊天记录 into 虐文、BE短篇、遗憾文学、分手文学、第一人称独白、小说化改写、小红书/朋友圈伤感文案, or wants emotional tension extracted from real conversations while preserving the core relationship dynamics.
---

# Chat To Angst Fiction

## Core Workflow

1. **Read the full chat data first.** Load the export, transcript, screenshots, or notes in chunks that cover the beginning, turning points, peak intimacy, breakdown, and ending. Never write before you understand the full arc.
2. **Protect privacy.** Replace real names, phone numbers, exact addresses, school/company identifiers, social handles, QQ/WeChat IDs, and private links with fictional or generic labels.
3. **Extract the emotional spine.** Identify: relationship status, speaker roles, the hidden want, the visible conflict, the turning point, the sentence that hurts most, and the ending emotion.
4. **Map evidence before writing.** Every emotional claim, descriptive detail, and scene should trace back to a timestamped message or observable pattern. For detailed rules, read `references/evidence-rules.md`.
5. **Choose a lens.** Pick one primary style unless the user specifies otherwise:
   - `第三人称短篇`: cinematic, restrained, good for complete narrative arcs.
   - `第一人称独白`: intimate, regret-heavy, good for confession or aftermath.
   - `聊天体虐文`: preserves message rhythm and adds only evidence-supported inner monologue.
   - `BE片段`: inevitable loss, no neat reconciliation.
6. **Write in Chinese.** Keep language natural, modern, emotionally precise. Prefer restraint over melodrama.
7. **Deliver output.** Default to Markdown in chat or a user-specified file. If the user wants an editable document, use `scripts/generate_docx.py` to generate DOCX.

## Evidence-Based Writing Rule

**Every sentence must survive the question: "Where in the chat record does this come from?"**

| Allowed when evidenced | Forbidden without evidence |
|---|---|
| Quote actual messages verbatim | Invent physical descriptions such as clothing, smell, or gestures |
| Use real timestamps from the record | Invent setting details such as curtains, light, weather, or room layout |
| Use real statistics such as message counts and time spans | Invent internal monologue from the other person |
| Interpret emotion from message patterns | Invent future events or hypothetical meetings |
| Reference real objects from chat | Invent scenes that are not anchored in messages |
| Mention chat features such as stickers, voice notes, images, and recalled messages | Claim what someone thought or felt when they did not say it |

When interpreting emotion, signal it as interpretation rather than fact: use "他大概……", "也许……", "可能……".

## Conversion Method

For long-form narrative from chat exports:

1. **Scene anchor:** use a real timestamp, first message, last message, or explicit turning point.
2. **Quote real dialogue.** Let the exchanged words carry the weight.
3. **Subtext from the narrator's side only.** Reveal what the narrator wanted but did not say when the record supports that silence. Do not invent the other person's inner state.
4. **Pattern as plot.** Use observable changes such as reply speed, message length, word choice, and initiative as the narrative engine.
5. **Knife sentence:** preserve the actual most painful line from the chat, anonymized if needed.
6. **Aftermath:** end with a real artifact or observable residue from the record, not an invented final scene.

## Style Rules

- Quote real messages verbatim whenever possible; authenticity carries more force than invented drama.
- Use only objects, links, images, games, nicknames, gifts, and recurring phrases that appear in the material.
- Use real timestamps and statistics as structural anchors when they are available.
- Prefer observable language like "她的回复从长句变成了一个字" over unsupported conclusions like "她越来越冷淡".
- Let asymmetry speak through counts, response timing, and initiative.
- Avoid tears, rain, alcohol, hospital beds, death, and reunion scenes unless the source material contains them.
- For "更虐一点": deepen inevitability and restraint by adding more evidence, not more melodrama.
- For "像真实发生的": quote more and invent less.

## Common Input Formats

### QQ/WeChat JSON Export

Use fields such as `time`, `timestamp`, `sender`, `content.text`, message type, and recalled/deleted markers when available.

```json
{
  "messages": [
    {
      "timestamp": 1729352712000,
      "time": "2024-10-19 08:45:12",
      "sender": {
        "uid": "anonymized_user_id",
        "name": "anonymized_name"
      },
      "type": "text",
      "content": { "text": "message text" },
      "recalled": false
    }
  ]
}
```

### Screenshot or Transcript

When only screenshots or text transcripts are available:

- Preserve speaker order and visible timestamps.
- Mark missing timestamps as approximate instead of pretending precision.
- Do not infer deleted, cropped, or hidden content.

## DOCX Output

To convert Markdown to DOCX:

```powershell
python scripts/generate_docx.py output.md output.docx
```

The script uses Microsoft YaHei, 10.5pt, and 1.5 line spacing by default.

## Safety Boundaries

- Minors in chat: keep content non-sexual and age-appropriate.
- Self-harm mentions: do not romanticize or intensify; write around care, distance, and aftermath.
- Requests to expose, humiliate, or identify a real person: refuse that framing and offer an anonymized version.
- Do not reproduce PII such as phone numbers, addresses, school names, company names, account IDs, or private links.
