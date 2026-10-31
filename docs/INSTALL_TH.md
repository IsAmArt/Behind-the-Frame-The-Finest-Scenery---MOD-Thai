# ติดตั้งมอดภาษาไทย — ทำตามทีละขั้น

[หน้าแรก](../README.md) · [English](INSTALL_EN.md) · [แก้ปัญหา](TROUBLESHOOTING_TH.md)

**Full Content — Public Pre-release** เนื้อหาไทยครบ แต่ QA ของ ZIP นี้ยังไม่ครบและมีปัญหาที่ทราบ ผู้เล่นเป็นผู้เปิดเกมเองทุกครั้ง

## 0. ตรวจ Vanilla ก่อนติดตั้งอะไรเพิ่ม

1. ติดตั้งเกม Steam หรือ Epic ที่จะเล่น แล้วเปิดเกมเดิมโดย **ไม่มีมอดและ BepInEx** ตรวจว่าเข้าเมนูได้ ถ้ามีมอดเดิม ให้ดู [กลับ Vanilla อย่างปลอดภัย](BACKUP_UNINSTALL_TH.md) ก่อน
2. ถ้าเข้าเมนูได้ ให้ปิดเกม แล้วค่อยดาวน์โหลดและติดตั้ง BepInEx รุ่นที่กำหนด
3. เปิดเกมตรวจ BepInEx อย่างเดียวให้ทำงานได้ แล้วปิดเกมก่อนดาวน์โหลดและคัดลอกมอดไทยตามขั้นตอนถัดไป

ถ้าเกม Vanilla จอดำตั้งแต่เปิด **อย่าเพิ่งติดตั้ง BepInEx/มอด** อ่าน [เกมเปิดแล้วจอดำตั้งแต่เริ่ม — วิธีตรวจสอบและแก้ไขเบื้องต้น](STARTUP_BLACK_SCREEN_TH.md) การรีเซต Registry ไม่ใช่ขั้นตอนติดตั้งปกติ ไม่ต้องทำทุกครั้ง

นี่คือคู่มือออนไลน์ล่าสุด; ZIP v1.0.0-rc1 ยังเป็นไฟล์เดิม

## 1. เตรียมตัวก่อนติดตั้ง

- เกม **Behind the Frame: The Finest Scenery บน Steam หรือ Epic Games Store สำหรับ Windows x64** ที่ติดตั้งและเปิดได้ตามปกติ
- ZIP **BepInEx 6.0.0-be.788 — Unity.IL2CPP-win-x64** และ ZIP **มอดภาษาไทย** เป็น **คนละไฟล์** ต้องมีทั้งสองอย่าง
- โปรแกรมแตก ZIP ของ Windows (คลิกขวา → **Extract All… / แยกทั้งหมด…**) หรือโปรแกรมที่รองรับ ZIP

ถ้าเคยลงมอดแล้ว ให้อ่าน [สำรองมอดรุ่นเก่า](BACKUP_UNINSTALL_TH.md) ก่อน ปิดเกมก่อนคัดลอกหรือเปลี่ยนไฟล์ ไม่ต้องเริ่ม New Game หรือลบเซฟ

## 2. ค้นหาโฟลเดอร์เกม — แยกตามร้านที่ติดตั้ง

### Steam

เปิดSteam → Library → คลิกขวาเกม → Properties… → Installed Files → Browse… แล้วหา **Behind the Frame.exe** บางชุดต้องเข้า **BehindTheFrame_PC_Steam** อีกชั้น

```text
โฟลเดอร์เกม Steam ที่ Browse เปิดให้/
└─ BehindTheFrame_PC_Steam/      ← ถ้ามีชั้นนี้ ให้เข้าไป
   ├─ Behind the Frame.exe      ← วางไฟล์ BepInEx ข้างนี้
   └─ Behind the Frame_Data/    ← ไม่วางมอดข้างใน
```

### Epic Games Store

เปิดEpic Games Launcher → Library → ปุ่ม **…** ของเกม → **Manage / จัดการ** แล้วหา **Open Install Location** หรือปุ่มรูปโฟลเดอร์ ถ้าUIต่างกัน ให้ดูInstallation locationแล้วเปิดตำแหน่งนั้นในFile Explorer หา **Behind the Frame.exe จริง** ในเกมที่ติดตั้ง อย่าเดาโฟลเดอร์จากร้านอื่น

```text
โฟลเดอร์ที่ติดตั้งเกม Epic/
├─ .egstore/                    ← ข้อมูลLauncher ไม่วางมอดตรงนี้
└─ โฟลเดอร์เกมที่มี EXEจริง/     ← อาจเป็นโฟลเดอร์นี้เองหรือชั้นย่อย
   ├─ Behind the Frame.exe      ← วางไฟล์ BepInEx ข้างนี้
   └─ Behind the Frame_Data/    ← ไม่วางมอดข้างใน
```

ผังเป็นตัวอย่างตำแหน่ง ไม่ใช่ภาพหน้าจอหรือการยืนยันว่าทุกbuildมีโครงสร้างเหมือนกัน หากEXEอยู่ที่ชั้นนอกให้ใช้ชั้นนอก ไม่สร้างโฟลเดอร์ตามผังเพิ่ม ไม่วางในSave, Behind the Frame_Data, .egstore หรือBepInEx/BepInEx ถ้าไม่พบEXEให้หยุดตรวจตำแหน่งก่อน

[ตัวอย่างเมนูSteam/Epicโดยผู้จัดจำหน่าย Microids](https://support.microids.com/en/support/solutions/articles/23000007351-finding-the-executable-file-exe-of-your-pc-game)

## 3. ติดตั้ง BepInEx

1. คลิกปุ่ม **ดาวน์โหลด BepInEx 6.0.0-be.788** บน [หน้าแรก](../README.md) หรือ [ลิงก์ทางการนี้](https://builds.bepinex.dev/projects/bepinex_be/788/BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.788%2B5b766a3.zip)
2. เปิดโฟลเดอร์ **Downloads / ดาวน์โหลด** คลิกขวาไฟล์ ZIP เลือก **Extract All… / แยกทั้งหมด…** แล้วคลิก **Extract / แยก** หาก Windows 11 ไม่แสดงเมนู ให้เลือก **Show more options / แสดงตัวเลือกเพิ่มเติม**
3. เปิดโฟลเดอร์ที่แตกแล้วจนเห็นไฟล์และโฟลเดอร์ข้างใน เช่น **winhttp.dll**, **doorstop_config.ini**, **BepInEx** และ **dotnet**
4. ปิดเกม เลือกไฟล์และโฟลเดอร์ **ทั้งหมดข้างใน ZIP ของ BepInEx** คลิกขวา **Copy / คัดลอก** แล้วเปิดโฟลเดอร์ที่มี **Behind the Frame.exe** คลิกพื้นที่ว่าง → **Paste / วาง** อย่าคัดลอกโฟลเดอร์ชื่อ ZIP ครอบลงไปอีกชั้น
5. ตรวจว่า **winhttp.dll** และ **BepInEx** อยู่ข้าง EXE ในระดับเดียวกัน ตามผังด้านล่าง
6. หลังVanillaเข้าเมนูได้ ให้เปิดผ่านSteamหรือEpic Games Launcherเพื่อตรวจBepInExแยกก่อนลงมอด รอเมนูเกมจริงตามหัวข้อเปิดครั้งแรกด้านล่าง
7. **ปิดเกมก่อนติดตั้งมอดไทย** ในขั้นถัดไป

ถ้ามี BepInEx หรือมอดอื่นอยู่แล้ว **อย่ากด Replace ทั้งหมดทันที** ให้สำรองและตรวจรุ่นก่อน ไม่ทับ `BepInEx/config/BepInEx.cfg` ของผู้เล่น ไม่ใช้รุ่น Mono, x86, BepInEx 5 หรือ Latest แทนโดยถือว่ารองรับ

[คู่มือ BepInEx IL2CPP ทางการ](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html) · Hash รุ่นที่ตรวจไว้: `F4CC496BD098A0DF4164B81E3737297707F13A47C2478DBA2F60EEFAB784817A`

## เปิด BepInEx ครั้งแรก — ยังไม่ลงมอดไทย

หลังวางไฟล์ BepInEx ทางการไว้ข้าง **Behind the Frame.exe** ให้ทำตามนี้:

1. **ยังไม่คัดลอกมอดไทย** เปิดเกมปกติผ่าน Steam หรือ Epic Games Launcher ที่ติดตั้งเกมไว้
2. อาจมีหน้าต่างสีดำแยกแสดงข้อความ ชื่อว่า **BepInEx console** ช่วงนี้ BepInEx กำลังเตรียม/สร้างไฟล์ที่จำเป็นสำหรับ Unity IL2CPP **ไม่ได้กำลังติดตั้งมอดไทย**
3. ครั้งแรกอาจนานกว่าการเปิดเกมปกติ ผู้จัดทำเคยเห็นข้อความสีเหลืองก่อนเกมเริ่ม แต่ข้อความ/สีและการแสดง console อาจต่างกัน **อย่าใช้สีเหลืองเป็นเงื่อนไขว่าทำสำเร็จ**
4. อย่าปิด console ขณะที่ยังเตรียมไฟล์และมีความคืบหน้า รอจน **เมนูเกมจริงปรากฏ** แล้วปิดเกมตามปกติ
5. หลังปิดเกมแล้วจึงแตก ZIP มอดไทยและคัดลอกโฟลเดอร์ BepInEx ของมอดไปยังตำแหน่งเดิม เปิดเกมอีกครั้ง → **Settings → Language → ไทย**

หากมี error การเตรียมไฟล์หยุด หรือเกมไม่เข้าเมนู อย่าถือว่าสำเร็จเพราะเห็นสีใดสีหนึ่ง เก็บข้อความผิดพลาด/ภาพ console และ Log ที่มี เช่น BepInEx/LogOutput.log หรือ .txt และ ErrorLog.log ก่อนลองใหม่ ไม่ปิดการป้องกันไวรัส ลบข้อมูล หรือรีเซต Registry ตามการเดา [คู่มือ BepInEx IL2CPP ทางการ](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html)

## 4. ติดตั้งมอดไทย

1. ดาวน์โหลด ZIP จากปุ่ม **ดาวน์โหลดมอดภาษาไทยฉบับเต็ม** บนหน้าแรก หรือใน Assets ของ [GitHub Releases](https://github.com/IsAmArt/Behind-the-Frame-The-Finest-Scenery---MOD-Thai/releases) เลือก `BehindTheFrameThai_v1.0.0-rc1_FULL.zip` ไม่ใช่ Source code (zip/tar.gz)
2. คลิกขวา ZIP มอด → **Extract All… / แยกทั้งหมด…** → **Extract / แยก** แยกไว้นอกโฟลเดอร์เกมก่อน
3. เปิดโฟลเดอร์ที่แตกออกมา ชุดนี้ชื่อ `BehindTheFrameThai_v1.0.0-rc1_FULL` แล้วหาโฟลเดอร์ **BepInEx** ที่อยู่ข้าง README
4. คลิกขวาที่ **BepInEx** ของมอด → **Copy / คัดลอก** กลับไปโฟลเดอร์ที่มี **Behind the Frame.exe** → **Paste / วาง** ให้รวมกับ BepInEx เดิม ไม่วางลงข้างใน BepInEx อีกที
5. ตรวจว่าไม่มี **BepInEx/BepInEx** ซ้อนกัน และมี DLL มอดนี้เพียงรุ่นเดียว หากมีไฟล์มอดเก่า ให้ทำ [ขั้นตอนสำรอง/อัปเดต](BACKUP_UNINSTALL_TH.md) ก่อนยืนยันแทนที่เฉพาะไฟล์มอดไทย
6. เปิดเกมผ่าน Steam หรือ Epic Games Launcher เข้า **Settings / ตั้งค่า → Language / ภาษา → ไทย** ไม่ต้องติดตั้งฟอนต์ลง Windows

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

ดู [แก้ปัญหา](TROUBLESHOOTING_TH.md) · [สำรอง/ถอนมอด](BACKUP_UNINSTALL_TH.md) · [ปัญหาที่ทราบ](../KNOWN_ISSUES.md) ZIP เผยแพร่ชุดนี้ยังไม่ได้รับรอง QA ในเกมครบทุกจุด และ **ทดสอบใช้งานเบื้องต้นสำเร็จทั้ง Steam และ Epic Games Store บน Windows x64 โดยผู้จัดทำ** แต่ยังไม่ใช่QAครบทุกบท/build ไม่รับรองทุกแพลตฟอร์ม
