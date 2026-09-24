# golinks

ข้อมูลของลิงก์ย่อ FileKit เปิดใช้ที่ https://patcharasitp.github.io/filekit/go/

ทุกไฟล์ใน `l/` เข้ารหัสด้วย AES-GCM กุญแจมาจากชื่อลิงก์ผ่าน PBKDF2 ชื่อไฟล์ก็มาจากชื่อลิงก์เช่นกัน
คนที่ไม่รู้ชื่อลิงก์จึงไม่รู้ว่าไฟล์ไหนคือลิงก์อะไร และอ่านปลายทางไม่ได้ วิธีทำงานเต็มอยู่ที่ `go/core.js` ในรีโป FileKit

ลิงก์ใหม่สร้างได้ 2 ทาง หน้า https://patcharasitp.github.io/filekit/go/new/ (วาง fine-grained token ที่เขียนได้เฉพาะรีโปนี้)
หรือ `node tools/golink.mjs add <ชื่อ> <ลิงก์ยาว>` ในรีโป FileKit

## กติกาของรีโปนี้ ห้ามเปลี่ยน

- ไม่เปิด GitHub Pages หน้าพาไปอ่านไฟล์ผ่าน raw.githubusercontent.com ซึ่งไม่รันโค้ดใด ๆ
  ถ้าเปิด Pages ใครก็ตามที่ถือ token ของหน้าสร้างลิงก์จะวางโค้ดบนโดเมนเดียวกับ FileKit Portfolio FlowKit LearnKit ได้
- ปิด GitHub Actions
- ruleset บน main กันลบ branch และกัน force push ไม่มีใครข้ามกฎได้
- `node tools/golink.mjs check --live` ในรีโป FileKit ตรวจ 3 ข้อนี้ให้ทุกครั้ง

## ถ้า token หลุด

1. ยกเลิก token ทันทีที่ https://github.com/settings/personal-access-tokens
2. เปิดประวัติ commit ที่ https://github.com/PatcharasitP/golinks/commits/main หา commit ที่ไม่ได้ทำเอง
3. revert commit นั้น หรือลบไฟล์ที่ถูกเพิ่มหรือแก้
4. ลิงก์ร้ายอาจยังพาไปได้อีกถึง 5 นาทีจาก cache ของ raw ถ้าร้ายแรงให้ปิดหน้าพาไปชั่วคราวผ่าน FileKit (cache ของ Pages 10 นาที)
