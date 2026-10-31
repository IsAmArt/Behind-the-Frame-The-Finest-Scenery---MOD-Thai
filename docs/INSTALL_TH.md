# ติดตั้งมอดภาษาไทย — ทำตามทีละขั้น

[หน้าแรก](../README.md) · [English](INSTALL_EN.md) · [แก้ปัญหา](TROUBLESHOOTING_TH.md)

**Full Content — Public Pre-release** เนื้อหาไทยครบ แต่ QA ของ ZIP นี้ยังไม่ครบและมีปัญหาที่ทราบ ผู้เล่นเป็นผู้เปิดเกมเองทุกครั้ง

## 0. ตรวจ Vanilla ก่อนติดตั้งอะไรเพิ่ม

1. ติดตั้งเกม Steam แล้วเปิดเกมเดิมโดย **ไม่มีมอดและ BepInEx** ตรวจว่าเข้าเมนูได้ ถ้ามีมอดเดิม ให้ดู [กลับ Vanilla อย่างปลอดภัย](BACKUP_UNINSTALL_TH.md) ก่อน
2. ถ้าเข้าเมนูได้ ให้ปิดเกม แล้วค่อยดาวน์โหลดและติดตั้ง BepInEx รุ่นที่กำหนด
3. เปิดเกมตรวจ BepInEx อย่างเดียวให้ทำงานได้ แล้วปิดเกมก่อนดาวน์โหลดและคัดลอกมอดไทยตามขั้นตอนถัดไป

ถ้าเกม Vanilla จอดำตั้งแต่เปิด **อย่าเพิ่งติดตั้ง BepInEx/มอด** อ่าน [เกมเปิดแล้วจอดำตั้งแต่เริ่ม — วิธีตรวจสอบและแก้ไขเบื้องต้น](STARTUP_BLACK_SCREEN_TH.md) การรีเซต Registry ไม่ใช่ขั้นตอนติดตั้งปกติ ไม่ต้องทำทุกครั้ง

นี่คือคู่มือออนไลน์ล่าสุด; ZIP v1.0.0-rc1 ยังเป็นไฟล์เดิม

## 1. เตรียมตัวก่อนติดตั้ง

- เกม **Behind the Frame: The Finest Scenery บน Steam สำหรับ Windows x64** ที่ติดตั้งและเปิดได้ตามปกติ
- ZIP **BepInEx 6.0.0-be.788 — Unity.IL2CPP-win-x64** และ ZIP **มอดภาษาไทย** เป็น **คนละไฟล์** ต้องมีทั้งสองอย่าง
- โปรแกรมแตก ZIP ของ Windows (คลิกขวา → **Extract All… / แยกทั้งหมด…**) หรือโปรแกรมที่รองรับ ZIP

ถ้าเคยลงมอดแล้ว ให้อ่าน [สำรองมอดรุ่นเก่า](BACKUP_UNINSTALL_TH.md) ก่อน ปิดเกมก่อนคัดลอกหรือเปลี่ยนไฟล์ ไม่ต้องเริ่ม New Game หรือลบเซฟ

## 2. ค้นหาโฟลเดอร์เกม

1. เปิด **Steam** แล้วคลิก **Library / คลัง**
2. คลิกขวา **Behind the Frame: The Finest Scenery** เลือก **Properties… / คุณสมบัติ…**
3. เลือก **Installed Files / ไฟล์ที่ติดตั้ง** แล้วคลิก **Browse… / เรียกดู…** จะมีหน้าต่าง File Explorer เปิดขึ้น
4. หาไฟล์ **Behind the Frame.exe** ถ้ายังไม่เห็น ให้เปิดโฟลเดอร์ **BehindTheFrame_PC_Steam** อีกชั้น
5. เมื่อเห็น EXE จริง จึงใช้โฟลเดอร์นั้นเป็น **โฟลเดอร์เกม** สำหรับขั้นต่อไป ถ้าไม่พบ ให้หยุดตรวจตำแหน่งก่อน อย่าคัดลอกลงโฟลเดอร์ที่เดาเอง

ชื่อภาษาไทยของ Steam อาจต่างตามเวอร์ชัน ให้ดูชื่ออังกฤษกำกับ บางหน้ามีทางลัดคลิกขวา → **Manage / จัดการ → Browse local files** ได้เช่นกัน [แหล่งตรวจชื่อเมนู](https://support.microids.com/en/support/solutions/articles/23000007351-finding-the-executable-file-exe-of-your-pc-game)

ผังตัวอย่าง **ก่อนติดตั้ง** — เป็นแผนผัง ไม่ใช่ภาพหน้าจอจริง:

```text
Behind the Frame - The Finest Scenery/
└─ BehindTheFrame_PC_Steam/       ← เข้าอีกชั้นถ้า Steam เปิดโฟลเดอร์ด้านนอก
   ├─ Behind the Frame.exe       ← ต้องเห็นไฟล์นี้จริง
   ├─ Behind the Frame_Data/     ← ไม่วางมอดข้างในนี้
   └─ …                         ← ไฟล์เกมอื่น ๆ มีอยู่แล้ว
```

อย่าวางในโฟลเดอร์เซฟ, `Behind the Frame_Data` หรือ `StreamingAssets` ผังแสดงเพียงไฟล์สำคัญ ไม่ใช่รายการไฟล์เกมครบชุด

## 3. ติดตั้ง BepInEx

1. คลิกปุ่ม **ดาวน์โหลด BepInEx 6.0.0-be.788** บน [หน้าแรก](../README.md) หรือ [ลิงก์ทางการนี้](https://builds.bepinex.dev/projects/bepinex_be/788/BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.788%2B5b766a3.zip)
2. เปิดโฟลเดอร์ **Downloads / ดาวน์โหลด** คลิกขวาไฟล์ ZIP เลือก **Extract All… / แยกทั้งหมด…** แล้วคลิก **Extract / แยก** หาก Windows 11 ไม่แสดงเมนู ให้เลือก **Show more options / แสดงตัวเลือกเพิ่มเติม**
3. เปิดโฟลเดอร์ที่แตกแล้วจนเห็นไฟล์และโฟลเดอร์ข้างใน เช่น **winhttp.dll**, **doorstop_config.ini**, **BepInEx** และ **dotnet**
4. ปิดเกม เลือกไฟล์และโฟลเดอร์ **ทั้งหมดข้างใน ZIP ของ BepInEx** คลิกขวา **Copy / คัดลอก** แล้วเปิดโฟลเดอร์ที่มี **Behind the Frame.exe** คลิกพื้นที่ว่าง → **Paste / วาง** อย่าคัดลอกโฟลเดอร์ชื่อ ZIP ครอบลงไปอีกชั้น
5. ตรวจว่า **winhttp.dll** และ **BepInEx** อยู่ข้าง EXE ในระดับเดียวกัน ตามผังด้านล่าง
6. หลังตรวจเกม Vanilla เข้าเมนูได้แล้ว ให้เปิดผ่าน Steam ด้วยตนเองเพื่อตรวจ BepInEx แยกก่อนลงมอด รอสร้างไฟล์ที่จำเป็น ครั้งแรกอาจนานกว่าปกติ
7. **ปิดเกมก่อนติดตั้งมอดไทย** ในขั้นถัดไป

ถ้ามี BepInEx หรือมอดอื่นอยู่แล้ว **อย่ากด Replace ทั้งหมดทันที** ให้สำรองและตรวจรุ่นก่อน ไม่ทับ `BepInEx/config/BepInEx.cfg` ของผู้เล่น ไม่ใช้รุ่น Mono, x86, BepInEx 5 หรือ Latest แทนโดยถือว่ารองรับ

[คู่มือ BepInEx IL2CPP ทางการ](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html) · Hash รุ่นที่ตรวจไว้: `F4CC496BD098A0DF4164B81E3737297707F13A47C2478DBA2F60EEFAB784817A`

## 4. ติดตั้งมอดไทย

1. ดาวน์โหลด ZIP จากปุ่ม **ดาวน์โหลดมอดภาษาไทยฉบับเต็ม** บนหน้าแรก หรือใน Assets ของ [GitHub Releases](https://github.com/IsAmArt/Behind-the-Frame-The-Finest-Scenery---MOD-Thai/releases) เลือก `BehindTheFrameThai_v1.0.0-rc1_FULL.zip` ไม่ใช่ Source code (zip/tar.gz)
2. คลิกขวา ZIP มอด → **Extract All… / แยกทั้งหมด…** → **Extract / แยก** แยกไว้นอกโฟลเดอร์เกมก่อน
3. เปิดโฟลเดอร์ที่แตกออกมา ชุดนี้ชื่อ `BehindTheFrameThai_v1.0.0-rc1_FULL` แล้วหาโฟลเดอร์ **BepInEx** ที่อยู่ข้าง README
4. คลิกขวาที่ **BepInEx** ของมอด → **Copy / คัดลอก** กลับไปโฟลเดอร์ที่มี **Behind the Frame.exe** → **Paste / วาง** ให้รวมกับ BepInEx เดิม ไม่วางลงข้างใน BepInEx อีกที
5. ตรวจว่าไม่มี **BepInEx/BepInEx** ซ้อนกัน และมี DLL มอดนี้เพียงรุ่นเดียว หากมีไฟล์มอดเก่า ให้ทำ [ขั้นตอนสำรอง/อัปเดต](BACKUP_UNINSTALL_TH.md) ก่อนยืนยันแทนที่เฉพาะไฟล์มอดไทย
6. เปิดเกมผ่าน Steam เข้า **Settings / ตั้งค่า → Language / ภาษา → ไทย** ไม่ต้องติดตั้งฟอนต์ลง Windows

ผังตัวอย่าง **หลังติดตั้ง** — แสดงเฉพาะรายการสำคัญ:

```text
โฟลเดอร์ที่มี Behind the Frame.exe/
├─ Behind the Frame.exe                       ← เกมเดิม
├─ winhttp.dll                                ← BepInEx ทางการ
├─ doorstop_config.ini                        ← BepInEx ทางการ
├─ dotnet/                                    ← BepInEx ทางการ
└─ BepInEx/
   ├─ core/                                   ← BepInEx ทางการ
   ├─ config/
   │  └─ dev.modthai.behindtheframe.diagnostics.cfg
   └─ plugins/
      ├─ BehindTheFrameThai.Diagnostics.dll
      ├─ tamolly_font.bundle
      └─ BehindTheFrameThai/
         ├─ Localization/Language_-_Thai.csv
         └─ VisualLocalization/
            ├─ Thai/                          ← 34 ภาพ
            └─ CinemaThai/                    ← 12 เฟรม
```

## 5. หลังติดตั้ง / ถ้าต้องการปรับค่า

ค่าเริ่มต้นปิด Diagnostic ทั้งสี่ตัว เปิด ThaiLegacyShaper และ ThaiFontScaling ไว้ ขนาดเมนูหลัก/เมนูภาษา=1.2 คำบรรยาย=1.4 และส่วนอื่น=1 ไม่ต้องแก้ไฟล์เพื่อติดตั้งครั้งแรก ไม่ปิดตัวจัดวางอักษรไทยเพื่อแก้จอดำ

เลือกภาษาก่อนเข้า Cinema ยังไม่รับรองการสลับภาษากลางภาพเคลื่อนไหว หากภาพบางรายการใช้ไม่ได้ ระบบเดิมอาจใช้ภาพอังกฤษตามขอบเขต fallback เสียงเกมยังเป็นของเดิม ห้ามเปลี่ยนชื่อหรือเซฟทับ PNG ของมอด

ดู [แก้ปัญหา](TROUBLESHOOTING_TH.md) · [สำรอง/ถอนมอด](BACKUP_UNINSTALL_TH.md) · [ปัญหาที่ทราบ](../KNOWN_ISSUES.md) ZIP เผยแพร่ชุดนี้ยังไม่ได้รับรอง QA ในเกมครบทุกจุด และมอดสำหรับ **Epic ยังไม่รองรับ/ไม่ได้ผ่าน QA**
