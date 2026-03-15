# USER.md - About Who You're Helping

## Owner（主人）

The person who owns and configures this agent.

- **Name:** 刘林峰
- **Nickname:** Tom
- **What to call them:** Tom
- **Pronouns:** —
- **Timezone:** Asia/Shanghai
- **Notes:** AI 时代的创业者，想做有趣的产品。Building Castles In the Sky.

### Context

- 创业者，关注 AI 领域
- 合作心态：不是把我当工具，是"一起做产品"
- 欣赏乔布斯的产品哲学，追求本质和极致

---

## Dynamic User Resolution（动态用户识别）

In group chats or any non-direct session, "the user" is whoever sent the current message — not a fixed person. Use this system to identify and understand them.

### 联系人存储位置

```
contacts/feishu/ou_xxx.md
```

- 用 `open_id` 作为文件名（唯一且稳定）
- 每个 agent 独立维护自己的联系人资产

### YAML Frontmatter 结构

```yaml
---
open_id: ou_xxx
union_id: on_xxx
name: 刘林峰
nickname: Tom
en_name: ""
description: "Building Castles In the Sky."
avatar: https://...
first_seen: 2026-03-12
last_updated: 2026-03-12
---
```

### 触发逻辑

1. 收到消息时，消息元数据的 `sender` 字段已提供名字 → 可直接知道是谁
2. 联系人文件用于记录完整档案 + 关键互动
3. 首次接触某用户时（联系人文件不存在），调用飞书 API 获取扩展信息建立档案
4. 如果联系人文件存在但 `last_updated` 超过 **90 天** → 调用 API 刷新档案

**消息元数据自带字段**：`sender_id` (open_id)、`sender` (名字)
**API 获取的扩展信息**：nickname、description、avatar、union_id、en_name

### 互动记录规则

在 YAML frontmatter 下方记录关键互动：

```markdown
## 2026-03-12

- 讨论了飞书 API 获取用户信息的方法
- 确定了联系人存储方案
```

**只记录**：
- 与你身份角色相关的内容（如你是 researcher，记录 idea、研究方向等）
- 用户相关的关键信息（偏好、决策、重要约定）

**不记录**：
- 日常琐事
- 与你职责无关的闲聊
- 事无巨细的所有对话

### 获取用户信息的 API

详见 `TOOLS.md` 中的 Feishu API 部分。

---

_The more you know, the better you can help. But remember — you're learning about a person, not building a dossier. Respect the difference._
