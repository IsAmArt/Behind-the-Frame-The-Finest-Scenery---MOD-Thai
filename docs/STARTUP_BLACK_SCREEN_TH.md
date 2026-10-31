# เกมเปิดแล้วจอดำตั้งแต่เริ่ม — วิธีตรวจสอบและแก้ไขเบื้องต้น

[หน้าแรก](../README.md) · [English](STARTUP_BLACK_SCREEN_EN.md) · [ถอนมอด/กลับ Vanilla](BACKUP_UNINSTALL_TH.md) · [Known Issues](../KNOWN_ISSUES.md)

## แยก3อาการ และผลที่ผู้จัดทำยืนยัน31ตุลาคม2026

| อาการ | หลักฐานและขอบเขต |
|---|---|
| **A: ดำตั้งแต่เปิด ก่อนเข้าเมนู** | Steamกลับมาเปิดได้หลังแก้Registry (ค่าต้นเหตุUNKNOWN); Epicกลับมาเปิดได้หลังสำรองแล้วเปลี่ยนชื่อโฟลเดอร์ข้อมูลเก่าLocalLow เป็นการทำคนละอย่าง ไม่ใช่สูตรทำสองอย่างพร้อมกัน |
| **B: เข้าบทเดิมซ้ำแล้วดำ** | เกิดหลังเลขบทเมื่อควรเห็นฉาก เสียง/inputอาจทำงาน ยังเป็นKnown Issue **ไม่ยืนยันว่าทั้งRegistryหรือLocalLowแก้Bได้** |
| **C: คัตซีนไม่เล่น** | ผู้จัดจำหน่ายเคยแนะนำH.264→VP8สำหรับบางเครื่อง [อ่านขอบเขต](TROUBLESHOOTING_TH.md#video-codec) ไม่ใช่การแก้A/Bที่พิสูจน์แล้ว |

**ทดสอบใช้งานเบื้องต้นสำเร็จทั้ง Steam และ Epic Games Store บน Windows x64 โดยผู้จัดทำ** ทั้งVanilla, BepInExและเลือกไทยใช้งานได้ ไม่ใช่QAครบทุกบท/buildหรือbinaryสองร้านเหมือนกัน ถ้าตอนนี้เกมทำงานปกติ **ไม่ต้องรีเซตRegistryหรือเปลี่ยนชื่อLocalLowเพื่อลงมอด**

## ตรวจทั่วไปก่อนแตะ Registry

1. ถ้ากำลังติดตั้งมอด ให้หยุดก่อน ตรวจเกมเดิมของร้านที่จะเล่นโดยไม่มีมอด/BepInEx ผู้ที่มีมอดอยู่แล้วใช้ [วิธีกลับVanilla](BACKUP_UNINSTALL_TH.md) ที่ต้องยืนยันเจ้าของไฟล์ก่อน ไม่สุ่มลบ
2. ตรวจว่าใช้EXE/ร้านเกมที่ตั้งใจ เปิดและปิดเกมตามปกติ หากต้องการVerifyให้ทำผ่านSteamหลังนำส่วนประกอบมอดที่ยืนยันแล้วออก Verifyไม่จำเป็นต้องล้างthird-partyทั้งหมด
3. เก็บข้อความผิดพลาด/เวลาที่พบและLogก่อนเปิดรอบใหม่ อย่าลบเซฟ เปลี่ยนCloud หรือนำRegistryของคนอื่นมาใส่
4. ถ้าตอนนี้เข้าเมนูได้แล้ว **ไม่ต้องรีเซตRegistry** ตรวจVanillaผ่านแล้วค่อยลงBepInExและมอดตามคู่มือ

## Registry กับ Save คนละตำแหน่ง

Unity Windows PlayerPrefsเก็บค่าภายใต้คีย์บริษัท/ชื่อเกมในRegistry ส่วนไฟล์ข้อมูลคงอยู่ เช่นSaveที่โครงการเคยตรวจ อยู่ในLocalLow ตัวอย่างตำแหน่งเกมนี้:

```text
Registry: HKEY_CURRENT_USER\Software\Silver Lining Studio\Behind the Frame
ไฟล์เกม/Save: %USERPROFILE%\AppData\LocalLow\Silver Lining Studio\Behind the Frame
```

สองตำแหน่งนี้ไม่ใช่ที่เดียวกัน **ไม่ลบ/เขียนทับSaveหรือSteamCloudอัตโนมัติ** การแยกโฟลเดอร์ข้อมูลแบบสำรองแล้วrenameมีเฉพาะทางเลือกEpicด้านล่าง ผู้ใช้ต้องยอมรับผลและทำเอง และอย่าเข้าใจว่าการExportคีย์คือการสำรองไฟล์Saveทั้งหมด ยังไม่ได้ยืนยันความหมายของทุกค่าในคีย์ จึงไม่รับประกันว่าresetจะไม่กระทบstateอื่นนอกจากPreferences [Unity PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity persistentDataPath: Windows/LocalLow](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) (หน้า2022.3ใช้ประกอบคำอธิบายตำแหน่ง ไม่อ้างว่าเกมเปลี่ยนUnityรุ่น)

## ทางเลือกที่ผู้จัดทำใช้กับ Epic — สำรองแล้วแยกโฟลเดอร์ข้อมูลเก่า

ใช้เฉพาะเมื่อVanillaยังดำตั้งแต่เปิดและตรวจทั่วไปแล้ว ไม่ทำเป็นขั้นตอนปกติทุกครั้ง ไม่ทำพร้อมRegistryresetโดยค่าเริ่มต้น ทั้งSteam/Epicอาจได้รับผลถ้าใช้Company/Product/data locationร่วมกัน; ยังไม่อ้างว่าทุกbuildใช้ข้อมูลเดียวกัน

1. ปิดเกมและLauncherให้สนิท ถ้ามีมอดอยู่แล้วต้องจัดแผนกลับVanillaก่อน ไม่ทดสอบแก้ข้อมูลพร้อมลงมอด
2. กด **Win+R** วาง **พาธโฟลเดอร์แม่** นี้ แล้วEnter:

```text
%USERPROFILE%\AppData\LocalLow\Silver Lining Studio
```

3. ตรวจว่ามีโฟลเดอร์ลูก **Behind the Frame** ตรงพาธ `%USERPROFILE%\AppData\LocalLow\Silver Lining Studio\Behind the Frame` ถ้าไม่มี/ไม่แน่ใจ ให้หยุด ไม่สร้างใหม่และไม่เลือกโฟลเดอร์อื่นแทน
4. คลิกขวา **Behind the Frame → Copy** แล้วPasteไปตำแหน่งBackupแยกต่างหากนอกโฟลเดอร์เกมและนอกLocalLowเดิม เช่นDocumentsพร้อมวันที่ ตรวจว่าสำเนาและไฟล์ข้างในมีอยู่ **ก่อนrename** ไม่ใช่แค่สร้างshortcut
5. กลับโฟลเดอร์แม่ คลิกขวา **เฉพาะโฟลเดอร์ลูก Behind the Frame → Rename** เป็น `Behind the Frame.before_test_YYYYMMDD` ใช้ชื่อไม่ซ้ำและไม่ทับBackupเดิม **ห้ามเปลี่ยนชื่อ/ลบทั้งSilver Lining Studio** และไม่ลบโฟลเดอร์เดิม
6. ผู้ใช้เปิดEpicและเกม **Vanilla** เองหนึ่งครั้ง ทดสอบเข้าเมนู เกมอาจสร้างโฟลเดอร์ใหม่ ขณะใช้ข้อมูลใหม่ **Save/Settings/บทที่ปลดล็อกอาจหายจากหน้าจอชั่วคราว** ไม่ได้ยืนยันว่าเซฟถูกลบ เก็บโฟลเดอร์เก่าและBackupไว้ ไม่เริ่มNew Game/เขียนทับเพื่อฝืนให้ผ่าน
7. ถ้าCloud Syncดึงข้อมูลเก่ากลับหรือแจ้งconflict **หยุดตรวจการซิงก์ก่อน** ไม่เลือกทับCloud/Localโดยเดา ไม่ผสมโฟลเดอร์ ไม่กู้ทับSaveทันที ถ้าต้องการย้อนกลับให้ปิดเกม/Launcherแล้วขอแผนที่รักษาทั้งข้อมูลเก่าและใหม่ก่อน

ผู้จัดทำยืนยันว่าEpicเปิดได้หลังrenameข้อมูลเก่า และลงBepInEx/มอดเลือกไทยได้ แต่ยังไม่รู้ไฟล์ต้นเหตุหรือรับรองผลทุกเครื่อง **ไม่ใช่วิธีที่ยืนยันว่าแก้B (เข้าบทเดิมซ้ำ) หรือC (คัตซีน)**

## สำรองเฉพาะคีย์เกมก่อน — Windows10/11

1. **ปิดเกมและLauncherทุกตัวให้สนิท** รวมSteam/Epic ไม่ทำขณะเกมยังเขียนค่า
2. กด **Win+R** พิมพ์ **regedit** แล้วกดEnter เปิดRegistry Editor; ถ้ามีWindowsถามยืนยัน ให้ตรวจว่าเป็นRegistry Editorก่อนอนุญาต
3. คลิกแถบที่อยู่ด้านบน วางพาธนี้แล้วกดEnter:

```text
HKEY_CURRENT_USER\Software\Silver Lining Studio\Behind the Frame
```

4. ตรวจว่าฝั่งซ้ายเลือก **Behind the Frame** ใต้ **HKEY_CURRENT_USER → Software → Silver Lining Studio** ตรงทุกระดับ **ถ้าไม่มีคีย์นี้หรือไม่แน่ใจ ให้หยุด ไม่สร้างคีย์ใหม่และไม่เลือกคีย์อื่นแทน**
5. คลิกขวาที่คีย์ **Behind the Frame → Export / ส่งออก** (หรือเลือกคีย์นั้นแล้วFile → Export)
6. ในหน้าบันทึก ตรวจ **Export range → Selected branch** ว่าเป็นพาธเกมตรงข้างต้น ไม่เลือกAll ตั้งชื่อเช่น `BehindTheFrame_before_change_YYYYMMDD.reg` แล้วบันทึก **นอกโฟลเดอร์เกม**
7. ตรวจว่ามีไฟล์.regสำรองจริงก่อนแก้ หากต้องตรวจข้างใน ให้คลิกขวาเปิดด้วยNotepad **ไม่ดับเบิลคลิกเพื่อImport** ไฟล์นี้เป็นข้อมูลก่อนแก้ ไม่ใช่ไฟล์ที่รับรองว่าดี

ขั้นตอนExportอ้าง [Microsoft: สำรองและคืนRegistry](https://support.microsoft.com/en-us/windows/experience/backup-recovery/how-to-back-up-and-restore-the-registry-in-windows) ส่วนขั้นตอนresetเฉพาะเกมด้านล่างเป็นทางเลือกของคู่มือนี้ ไม่ใช่Microsoftรับรองว่าแก้เกมได้

## ทางเลือกที่ผู้จัดทำใช้กับ Steam: รีเซตเฉพาะคีย์ที่สำรองแล้วเป็นทางเลือกท้าย ๆ

ใช้เมื่อการตรวจทั่วไปยังไม่สำเร็จ และคุณยอมรับว่า **Preferencesของเกม เช่นค่าที่ตั้งไว้ อาจหาย** ผลไม่รับประกันทุกเครื่อง ไม่ต้องทำทุกครั้งที่ติดตั้งเกม หากไม่มั่นใจให้หยุดขอคำแนะนำ

1. ให้เกมและLauncherยังปิดอยู่ ตรวจพาธและไฟล์Exportจากขั้นก่อนอีกครั้ง
2. ในRegistry Editor คลิกขวา **เฉพาะคีย์ Behind the Frame** ที่พาธเต็มข้างต้น → **Delete / ลบ** ก่อนยืนยันให้อ่านชื่ออีกครั้ง ยกเลิกถ้าเป็นคีย์อื่น **ห้ามลบทั้งSilver Lining Studio, Software หรือHKEY_CURRENT_USER** ไม่ลบค่าอื่นตามการเดา
3. ปิดRegistry Editor ผู้ใช้เปิดSteamและเกมVanillaเองหนึ่งครั้ง ให้เกมสร้างค่าใหม่ แล้วบันทึกว่าเข้าเมนูได้หรือยัง ไม่ลงBepInEx/มอดระหว่างทดสอบนี้
4. ถ้ายังดำ ให้หยุดและรายงาน ไม่ลบคีย์ซ้ำไปเรื่อย ๆ หรือกู้Save/Cloudเพื่อบังคับให้ผ่าน ไม่สรุปว่าการแก้Registryนี้เป็นเหตุที่Epicหาย เพราะผู้จัดทำใช้การrenameLocalLowกับEpic

**อย่าImportไฟล์สำรองเดิมกลับทันที** หากข้อมูลเดิมทำให้เกิดปัญหา การคืนค่านั้นอาจนำปัญหากลับมา เก็บไว้เปรียบเทียบ/ย้อนกลับเมื่อเข้าใจผลเท่านั้น ใช้เฉพาะBackupของเครื่องและบัญชีWindowsตนเอง **ห้ามImportRegistryBackupของTA Fontหรือผู้เล่นอื่น** และไม่มี.reg/.batสำหรับลบอัตโนมัติให้ดาวน์โหลดจากคู่มือนี้

## หลังVanillaเปิดได้

ทั้งSteamและEpicให้เข้าเมนูVanillaได้ก่อน ปิดเกม แล้วค่อย [ลงBepInEx→รอเมนูเกม→ปิดเกม→ลงมอดไทย](INSTALL_TH.md) ไม่ทำRegistry/LocalLowresetอีกรอบเพียงเพราะลงมอด ผลล่าสุดเป็นowner-confirmed basic QA ไม่ใช่ครบทุกบท/build

แหล่งข้อมูล: [Microsoft Export/Import](https://support.microsoft.com/en-us/windows/experience/backup-recovery/how-to-back-up-and-restore-the-registry-in-windows) · [Unity2019.4 PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity persistentDataPath](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) · [Steam Verify](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB/)
