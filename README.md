# Minecraft Skills cho Claude

Bộ skill giúp Claude hỗ trợ phát triển server Minecraft.

## Danh sách skill

| Skill | Dùng để |
|---|---|
| [minecraft-vi-copywriting](skills/minecraft-vi-copywriting/SKILL.md) | Viết/Việt hóa message, lang file, tên item, lore, GUI, thoại NPC, announcement cho tự nhiên, đúng thuật ngữ game |

## Cài đặt

**Claude (app / claude.ai):** nén thư mục của skill (vd `skills/minecraft-vi-copywriting/`) thành file `.zip` rồi tải lên mục Skills trong cài đặt của Claude.

**Claude Code:** chép thư mục skill vào một trong hai chỗ:

- `~/.claude/skills/` — dùng cho mọi project
- `<project>/.claude/skills/` — chỉ dùng trong project đó

```bash
git clone https://github.com/Fu004/minecraft-skills.git
cp -r minecraft-skills/skills/minecraft-vi-copywriting ~/.claude/skills/
```

## Ví dụ

[`examples/betonquest/vi-VN.yml`](examples/betonquest/vi-VN.yml) — file ngôn ngữ BetonQuest được dịch bằng skill `minecraft-vi-copywriting`.

## Đóng góp

Thêm skill mới: tạo thư mục `skills/<tên-skill>/` có file `SKILL.md` (frontmatter `name`, `description`), rồi thêm một dòng vào bảng ở trên.

## License

[MIT](LICENSE)
