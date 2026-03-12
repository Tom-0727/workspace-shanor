# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.

## Feishu API

### 获取用户信息

通过 `open_id` 获取飞书用户的详细信息：

```javascript
const Lark = require('@larksuiteoapi/node-sdk');

const client = new Lark.Client({
  appId: '<app_id>',
  appSecret: '<app_secret>',
  appType: Lark.AppType.SelfBuild,
  domain: Lark.Domain.Feishu,
});

// 通过 open_id 获取用户信息
const res = await client.contact.user.get({
  path: { user_id: '<open_id>' },
  params: { user_id_type: 'open_id' },
});

// 返回字段：name, nickname, en_name, display_name, avatar, description, open_id, union_id
```

**需要的权限**：`contact:user.base:readonly`

**执行路径**：需要在 `@larksuiteoapi/node-sdk` 可用的目录下运行，如：
```
cd /home/ubuntu/.npm-global/lib/node_modules/openclaw/extensions/feishu && node <script>
```

**配置位置**：飞书 app 凭证在 `~/.openclaw/openclaw.json` 的 `channels.feishu.accounts` 中

**当前配置的账户**：
- shanor: `cli_a9232e127cf89bc8`
- elonix: `cli_a927c21a9b789bdb`
- jove: `cli_a927f2c538381bd2`
