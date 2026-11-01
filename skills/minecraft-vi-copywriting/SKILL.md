---
name: minecraft-vi-copywriting
description: Viết lại/viết mới chữ tiếng Việt trong server Minecraft (messages.yml, vi.yml, lang, config item: name, lore, GUI, NPC, announcement) cho tự nhiên, đúng thuật ngữ game, đúng chất game thủ Việt.
---

# Văn phong tiếng Việt cho server Minecraft

Mục tiêu: mọi chữ người chơi thấy phải đọc như **một người admin thân thiện đang nói chuyện** — không như văn bản hành chính, không như Google Dịch, cũng không suồng sã thô lỗ. Thuật ngữ game phải khớp với bản tiếng Việt chính thức của Minecraft để người chơi nhận ra ngay.

Dùng skill này khi sửa hoặc viết mới: `messages.yml`, `vi.yml`, `lang/*.yml`, `messages_vi.properties`, file config item (display-name, lore), GUI/menu, hologram, scoreboard, tab, NPC dialogue, broadcast/announcement, tutorial, title/actionbar.

---

## 1. Quy trình

1. **Đọc cả file trước khi sửa.** Xác định:
   - Cú pháp màu: legacy `&a` / `§a`, hex `&#RRGGBB`, hay MiniMessage `<green>`, `<gradient:...>`. Giữ đúng cú pháp file đang dùng, không trộn.
   - Placeholder: `%player%`, `{0}`, `{player}`, `<player>`, `%vault_eco_balance%`... — ghi lại danh sách.
   - Xưng hô và giọng đang dùng (thường là "bạn"). Nếu file đã có giọng riêng nhất quán, theo giọng đó.
   - Nếu dự án có file thuật ngữ (vd `docs/thuat-ngu.md`, `glossary.md`) thì đọc và tuân theo — nó được ưu tiên hơn mọi nguồn khác.
2. **Tra thuật ngữ** cho tên block/item/mob/hiệu ứng/phù phép/chỉ số xuất hiện trong file theo mục 2.
3. **Phân loại từng dòng** theo mục 4 (lỗi, thành công, thông tin, hướng dẫn, thoại NPC, thông báo, tên item, lore, nút GUI, title/actionbar).
4. **Viết lại** theo mục 3 + mục 4. Dòng nào đã ổn thì **giữ nguyên** — không sửa cho có.
5. **Kiểm tra kỹ thuật** (mục 6), validate file.
6. **Báo cáo** theo mục 7.

---

## 2. Nguồn tham khảo — lấy THUẬT NGỮ, không lấy VĂN PHONG

Các bản Việt hóa có sẵn rất tốt để thống nhất từ ngữ, nhưng câu cú của chúng thường dịch sát từ tiếng Anh ("Số dư hợp lệ không đủ", "Việc xử lí yêu cầu dịch chuyển đã bị hủy"). Vì vậy: **mượn từ, không mượn câu.**

Thứ tự ưu tiên khi chọn từ:

1. **File thuật ngữ của dự án** (nếu có).
2. **Minecraft vanilla `vi_vn`** — nguồn chuẩn cho tên block, item, mob, hiệu ứng, phù phép, chỉ số, chế độ chơi, độ khó. Người chơi để client tiếng Việt sẽ thấy đúng các từ này trong game, nên lore/tin nhắn phải khớp.
   - Tra tại: `https://raw.githubusercontent.com/InventivetalentDev/minecraft-assets/<phiên bản>/assets/minecraft/lang/vi_vn.json` (vd `<phiên bản>` = `1.21`). File lớn — tìm theo key (`item.minecraft.diamond_sword`, `effect.minecraft.speed`, `enchantment.minecraft.sharpness`, `attribute.name.generic.attack_damage`, `gameMode.creative`...) thay vì đọc hết.
   - **Không đoán** tên vanilla từ trí nhớ khi không chắc — tra file, hoặc đánh dấu "cần xác nhận" trong báo cáo.
3. **EssentialsX `messages_vi.properties`** — tham khảo từ cho khái niệm plugin phổ biến (dịch chuyển, biệt danh, điểm hồi sinh, thư...): `https://raw.githubusercontent.com/EssentialsX/Essentials/2.x/Essentials/src/main/resources/messages_vi.properties`.
4. Cách game thủ Việt thực sự nói (mục 3).

### Thuật ngữ đã đối chiếu

Từ vanilla `vi_vn` (1.21) — dùng đúng như vậy trong lore/chỉ số:

| Tiếng Anh | vi_vn |
|---|---|
| Armor | Giáp |
| Armor Toughness | Độ bền áo giáp |
| Attack Damage | Sức tấn công |
| Attack Speed | Tốc độ tấn công |
| Max Health | Sinh lực tối đa |
| Movement Speed | Tốc độ |
| Knockback Resistance | Kháng đẩy lùi |
| Luck | Vận may |
| Mining Efficiency | Hiệu quả đào |
| Anvil | Cái đe |
| Ancient Debris | Mảnh vỡ cổ đại |
| Nether, The End | giữ nguyên "Nether", "The End" |

Từ EssentialsX vi (tham khảo khái niệm):

| Khái niệm | EssentialsX vi | Gợi ý cho chat/GUI |
|---|---|---|
| teleport | Dịch chuyển | "dịch chuyển" hoặc "tp" (chat nhanh) |
| enchantment | Phù phép | Phù phép |
| inventory | Túi | Túi đồ |
| item | Vật phẩm | "Vật phẩm" trong GUI/tiêu đề, "đồ" trong câu chat |
| nickname | Biệt danh | Biệt danh |
| spawn point / bed | Điểm hồi sinh | Điểm hồi sinh |
| gamemode | Chế độ chơi (Sinh tồn, Sáng tạo, Phiêu lưu) | giữ như vậy |
| ender chest | Rương ender | Rương ender |
| kit | Bộ dụng cụ | **"kit"** — trùng tên lệnh /kit, game thủ quen gọi vậy |
| experience | Kinh nghiệm | Kinh nghiệm / EXP |
| offline | Ngoại tuyến | **"offline"** |
| server | Máy chủ | **"server"** |

Quy tắc chung: **tên thứ có trong game (block, item, mob, hiệu ứng, phù phép, chỉ số) → theo vanilla vi_vn. Khái niệm server/plugin mà game thủ gọi bằng tiếng Anh (kit, warp, home, rank, spawn, server, online/offline, AFK, PvP, top) → giữ tiếng Anh.** Chọn xong thì dùng một từ duy nhất cho cả server.

### Mượn từ nhưng sửa câu — ví dụ từ EssentialsX vi

| Bản Việt hóa gốc | Viết lại |
|---|---|
| Bạn không có quyền để dùng lệnh này. | Bạn chưa có quyền dùng lệnh này. |
| Số dư hợp lệ không đủ. | Bạn không đủ tiền. |
| Bạn không thể thanh toán cho người chơi ngoại tuyến. | {0} đang offline, không chuyển tiền được. |
| Bạn không thể nhập lệnh đó trong {0}. | Đợi {0} nữa mới dùng lại được. |
| Dịch chuyển sẽ bắt đầu trong {0}. Đừng di chuyển. | Đứng yên {0}, sắp dịch chuyển... |
| Việc xử lí yêu cầu dịch chuyển đã bị hủy. | Đã hủy dịch chuyển vì bạn di chuyển. |
| Người chơi {0} chưa bao giờ vào máy chủ. | {0} chưa vào server lần nào. |
| Công cụ này còn {0} lần sử dụng nữa. | Công cụ này còn dùng được {0} lần. |
| Bạn không thể dùng bộ dụng cụ này trong {0}. | {0} nữa mới nhận lại kit này được. |
| Túi của bạn đã đầy. | Túi đồ đầy rồi, dọn bớt nhé. |
| Essentials đã được tải lại {0}. | Đã reload Essentials {0}. |

Khi viết lại file `messages_vi.properties` của plugin, giữ các escape của `.properties` (`\:`, `\!`, `''` với MessageFormat).

---

## 3. Nguyên tắc giọng văn

**Tự nhiên, ngắn, rõ việc cần làm.**

- **Xưng hô mặc định:** hệ thống gọi người chơi là "bạn", không xưng gì (hoặc "server" khi cần). Không dùng "Quý khách", "Người chơi" để gọi trực tiếp. Không dùng "mày/tao" trừ khi là thoại NPC có tính cách rõ ràng.
- **Ngắn trước, đầy đủ sau.** Cắt các cụm thừa: "để có thể", "thực hiện", "tiến hành", "việc...", "đã được ... thành công", "hiện tại", "một cách", "hợp lệ".
- **Chủ động thay bị động:** "đã bị hủy" → "đã hủy"; "đã được tải lại" → "đã reload".
- **Nói việc cần làm, không chỉ nói lỗi.** "Sai cú pháp" → "Dùng: /pay <tên> <số tiền>". Có lý do thì nói lý do.
- **Ưu tiên từ thuần Việt / từ game thủ hay dùng** hơn Hán-Việt nặng hay từ dịch máy: "sử dụng" → "dùng"; "hoàn tất" → "xong"; "không hợp lệ" → "không đúng" / chỉ rõ đúng là gì; "trực tuyến/ngoại tuyến" → "online/offline"; "máy chủ" → "server". (Ngoại lệ: tên thứ trong game vẫn theo vanilla vi_vn — mục 2.)
- **Trợ từ (nhé, nha, đó, rồi, nè, thôi):** dùng để mềm câu, nhưng **tối đa một trợ từ mỗi câu** và không phải câu nào cũng có. Cảnh báo nghiêm trọng / ban / kick thì không dùng trợ từ.
- **Chấm than tiết chế:** tối đa một `!`, chỉ cho tin vui hoặc sự kiện. Không `!!!`.
- **Viết hoa kiểu Việt:** chỉ viết hoa chữ đầu câu và tên riêng. Tên item/tên sự kiện/tiêu đề GUI được viết hoa từng chữ. Tránh ALL CAPS trừ nhãn ngắn kiểu `[VIP]`, `MỚI`.
- **Không thô:** không chửi thề, không mỉa mai người chơi, không teencode ("ko", "dc", "j", "z"), không viết tắt khó hiểu.
- **Nhất quán:** cùng một khái niệm dùng một từ trong toàn server (đã chọn "xu" thì đừng lẫn "coin"/"tiền").
- **Số ít/số nhiều:** tiếng Việt không chia số nhiều — các key kiểu `day`/`days` dịch giống nhau ("ngày").

### Dấu hiệu "văn máy" cần sửa

| Văn máy | Tự nhiên hơn |
|---|---|
| Vui lòng ... | (bỏ, hoặc chuyển thành câu mời: "... nhé") |
| ... đã được thực hiện thành công. | Đã ... / ... xong rồi. |
| Việc ... đã bị hủy. | Đã hủy ... (kèm lý do) |
| Đã xảy ra lỗi. Vui lòng thử lại sau. | Có lỗi rồi, thử lại sau chút nhé. Vẫn lỗi thì báo admin. |
| Người chơi được chỉ định không tồn tại. | Không tìm thấy người chơi %player%. |
| Lỗi: Đầu vào không hợp lệ. / Số không hợp lệ. | Nhập số thôi, ví dụ: 10 |
| Cần phải là một số khác không. | Số lượng phải lớn hơn 0. |
| Thanh Kiếm Của Lửa | Kiếm Lửa / Hỏa Kiếm |

---

## 4. Theo từng loại chữ

**Lỗi / từ chối** — ngắn, bình tĩnh, chỉ cách khắc phục. Màu đỏ/cam.
- `Bạn phải chờ %time% giây trước khi có thể sử dụng lại.` → `Từ từ đã, %time%s nữa mới dùng lại được.`

**Thành công** — xác nhận gọn, kèm kết quả cụ thể.
- `Giao dịch đã được hoàn tất thành công!` → `Đã chuyển %amount% xu cho %target%.`

**Thông tin / trạng thái** — nói thẳng thông tin.
- `Người chơi %player% hiện tại không trực tuyến.` → `%player% đang offline.`

**Hướng dẫn / tutorial** — từng bước, động từ đầu câu, mỗi dòng một ý, dẫn lệnh cụ thể.
- `Để có thể mở khóa tính năng này, bạn cần phải đạt được cấp độ 10.` → `Lên cấp 10 để mở khóa.`
- Nhiều bước: `1. Gõ /is create để tạo đảo` / `2. Chặt cây, làm bàn chế tạo` / `3. Gõ /is help nếu bí`

**Thoại NPC** — có cá tính theo nhân vật, được dùng xưng hô hợp vai ("ta – ngươi", "tôi – cậu", "chú – cháu"), nhưng dễ hiểu và ≤ 2 dòng chat mỗi câu. Nhân vật nào giữ giọng đó xuyên suốt.
- `Xin chào người chơi. Tôi có một nhiệm vụ dành cho bạn.` → `Ê, cậu kia! Rảnh không? Tôi đang cần người giúp một chuyện.`

**Announcement / broadcast** — có hook ở đầu, nói rõ cái gì – khi nào – ở đâu – làm gì. 1–3 dòng.
- `Sự kiện Boss Thế Giới sẽ bắt đầu sau 5 phút. Hãy chuẩn bị.` → `5 phút nữa Boss Thế Giới xuất hiện! Gõ /warp boss, rủ team đi cùng.`

**Tên item** — 1–4 chữ, gợi hình, không dùng "Của". Hán-Việt được phép cho item hiếm/huyền thoại (Hỏa Long Kiếm, Băng Tâm Giáp) nhưng đừng ghép vô nghĩa. Item cơ bản/biến thể vanilla thì bám tên vanilla vi_vn. Viết hoa từng chữ.

**Lore** — mỗi dòng ≤ ~35 ký tự hiển thị. Thứ tự gợi ý:
1. 1–2 dòng flavor (xám, nghiêng) — ngắn, có hồn.
2. Dòng trống.
3. Chỉ số gọn, dùng tên chỉ số vanilla: `+10% Sức tấn công`, `+2 Giáp`, `+15% Tốc độ`.
4. Dòng trống + cách dùng: `Chuột phải để dùng`.
5. Độ hiếm cuối cùng.

**Nút GUI / tiêu đề menu** — 1–3 chữ: `Mua`, `Bán hết`, `Quay lại`, `Trang sau`, `Xác nhận`. Lore của nút nói hệ quả: `Click để mua 1 cái` / `Shift-click: mua 64`.

**Title / subtitle / actionbar** — cực ngắn (title ≤ ~20 ký tự, subtitle/actionbar ≤ ~40).

**Tiến độ nhiệm vụ** — mẫu "Còn {n} ... cần ...": `Còn 5 khối cần phá`, `Còn 3 con cừu cần xén lông`.

---

## 5. Đừng làm quá

- Không biến mọi câu thành đùa cợt hay meme — server vẫn cần rõ ràng.
- Không "trẻ trâu hóa" ("bro", "ngon lành cành đào"...) trừ khi file đã dùng giọng đó.
- Không thêm emoji/ký tự đặc biệt nếu file chưa dùng; nếu dùng, kiểm tra font resource pack hiển thị được.
- Không đổi nghĩa gốc, không bỏ thông tin (số liệu, điều kiện, lệnh).
- Không "Việt hóa" tên lệnh, tham số lệnh hoặc tên thế giới/warp thật.
- Cẩn thận với chuỗi **người chơi phải gõ lại** (vd tiền tố `password:` của BetonQuest): dịch sang tiếng có dấu sẽ bắt người chơi gõ dấu — đánh dấu để người dùng quyết.

---

## 6. Kiểm tra kỹ thuật (bắt buộc)

- **Không đổi key**, chỉ đổi value. Giữ cấu trúc list (lore là list thì vẫn là list).
- **Giữ nguyên 100% placeholder** và tag màu/format, kể cả tiền tố kiểu `@[legacy]`, `@[minimessage]`. Được đổi vị trí placeholder trong câu, không được đổi tên hay bỏ.
- Đổi trật tự câu thì đặt lại màu sau placeholder (vd `&e%player% &7đã vào server`; MiniMessage: `<secondary>{0}<primary> ...`).
- YAML: chuỗi bắt đầu bằng `&`, `%`, `{`, `<`, `[`, `*`, `!`, `@` hoặc chứa `: ` / ` #` phải đặt trong nháy. Trong nháy đơn, `'` viết thành `''`.
- `.properties` (EssentialsX, LuckPerms...): giữ `\:`, `\!`, và `''` khi chuỗi dùng MessageFormat `{0}`.
- Giữ `\n` và xuống dòng giống bản gốc nếu plugin cần.
- Không đụng các dòng cấu hình như `configVersion`.
- File lưu **UTF-8 không BOM**, tiếng Việt đủ dấu, Unicode dựng sẵn (NFC).
- Validate YAML sau khi sửa: `python -c "import yaml,sys; yaml.safe_load(open(sys.argv[1],encoding='utf-8'))" <file>`.
- So bộ key và placeholder theo từng key giữa bản cũ và mới bằng regex `%[^%\s]+%|\{[^}]+\}|<[^>]+>|&[0-9a-fk-or]|&#[0-9a-fA-F]{6}|@\[[a-z]+\]`.
- Thấy lỗi sẵn trong bản gốc (vd hai mô tả lệnh bị đặt ngược) thì sửa cho đúng nghĩa và ghi rõ trong báo cáo.

---

## 7. Định dạng báo cáo

```
Đã sửa 23/80 dòng trong messages.yml (57 dòng giữ nguyên vì đã ổn).

| Key | Trước | Sau |
|---|---|---|
| economy.not-enough | Bạn không đủ số dư để thực hiện giao dịch này. | Bạn không đủ tiền (cần %price%). |

Thuật ngữ đã tra vanilla vi_vn: <key> → "<từ>"

Cần bạn xác nhận:
- `quest.npc-3`: không rõ NPC này là ai — đang giữ giọng trung tính.
```
