# เกมเปิดแล้วจอดำตั้งแต่เริ่ม — วิธีตรวจสอบและแก้ไขเบื้องต้น

[หน้าแรก](../README.md) · [English](STARTUP_BLACK_SCREEN_EN.md) · [ถอนมอด/กลับ Vanilla](BACKUP_UNINSTALL_TH.md) · [Known Issues](../KNOWN_ISSUES.md)

## แยกก่อนว่าเป็นอาการใด

| อาการ | หลักฐานและขอบเขต |
|---|---|
| **A: ดำตั้งแต่เปิด ก่อนเข้าเมนู** | ผู้ใช้เคยพบทั้ง Steamที่ติดตั้งใหม่ไม่มีBepInEx/มอด และ Epic Vanilla หลังผู้ใช้แก้Registryของเกม Steamเปิดได้แล้ว แต่ยังไม่รู้ค่าต้นเหตุและยังไม่ทดสอบEpicใหม่ |
| **B: เข้าบทเดิมซ้ำแล้วดำ** | กลับเมนูแล้วเข้าบทเดิมโดยยังไม่ปิดเกม เลขบทอาจแสดงปกติแต่ดำเมื่อควรเห็นฉาก เสียง/inputอาจทำงาน เป็นอีกKnown Issue; **ไม่มีหลักฐานว่าRegistryresetแก้Bได้** |

นี่เป็นผลที่ผู้ใช้ยืนยัน ไม่ใช่การระบุroot causeหรือผลรับรองทุกเครื่อง ไม่ถือว่ามอด/เกมต้นฉบับเป็นต้นเหตุจากอาการเดียว Epicยัง **NOT VALIDATED / ไม่รองรับมอด** จนมีQAที่เกี่ยวข้อง

## ตรวจทั่วไปก่อนแตะ Registry

1. ถ้ากำลังติดตั้งมอด ให้หยุดก่อน ตรวจเกมSteamเดิมโดยไม่มีมอด/BepInEx ผู้ที่มีมอดอยู่แล้วใช้ [วิธีกลับVanilla](BACKUP_UNINSTALL_TH.md) ที่ต้องยืนยันเจ้าของไฟล์ก่อน ไม่สุ่มลบ
2. ตรวจว่าใช้EXE/ร้านเกมที่ตั้งใจ เปิดและปิดเกมตามปกติ หากต้องการVerifyให้ทำผ่านSteamหลังนำส่วนประกอบมอดที่ยืนยันแล้วออก Verifyไม่จำเป็นต้องล้างthird-partyทั้งหมด
3. เก็บข้อความผิดพลาด/เวลาที่พบและLogก่อนเปิดรอบใหม่ อย่าลบเซฟ เปลี่ยนCloud หรือนำRegistryของคนอื่นมาใส่
4. ถ้าตอนนี้เข้าเมนูได้แล้ว **ไม่ต้องรีเซตRegistry** ตรวจVanillaผ่านแล้วค่อยลงBepInExและมอดตามคู่มือ

## Registry กับ Save คนละตำแหน่ง

Unity Windows PlayerPrefsเก็บค่าภายใต้คีย์บริษัท/ชื่อเกมในRegistry ส่วนไฟล์ข้อมูลคงอยู่ เช่นSaveที่โครงการเคยตรวจ อยู่ในLocalLow ตัวอย่างตำแหน่งเกมนี้:

```text
Registry: HKEY_CURRENT_USER\Software\Silver Lining Studio\Behind the Frame
ไฟล์เกม/Save: %USERPROFILE%AppDataLocalLowSilver Lining StudioBehind the Frame
```

สองตำแหน่งนี้ไม่ใช่ที่เดียวกัน **อย่าลบ/ย้าย/รีเซตSaveหรือSteamCloud** เพื่อทำตามคู่มือนี้ และอย่าเข้าใจว่าการExportคีย์คือการสำรองไฟล์Saveทั้งหมด ยังไม่ได้ยืนยันความหมายของทุกค่าในคีย์ จึงไม่รับประกันว่าresetจะไม่กระทบstateอื่นนอกจากPreferences [Unity PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity persistentDataPath: Windows/LocalLow](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) (หน้า2022.3ใช้ประกอบคำอธิบายตำแหน่ง ไม่อ้างว่าเกมเปลี่ยนUnityรุ่น)

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

## ทางเลือกท้าย ๆ: รีเซตเฉพาะคีย์ที่สำรองแล้ว

ใช้เมื่อการตรวจทั่วไปยังไม่สำเร็จ และคุณยอมรับว่า **Preferencesของเกม เช่นค่าที่ตั้งไว้ อาจหาย** ผลไม่รับประกันทุกเครื่อง ไม่ต้องทำทุกครั้งที่ติดตั้งเกม หากไม่มั่นใจให้หยุดขอคำแนะนำ

1. ให้เกมและLauncherยังปิดอยู่ ตรวจพาธและไฟล์Exportจากขั้นก่อนอีกครั้ง
2. ในRegistry Editor คลิกขวา **เฉพาะคีย์ Behind the Frame** ที่พาธเต็มข้างต้น → **Delete / ลบ** ก่อนยืนยันให้อ่านชื่ออีกครั้ง ยกเลิกถ้าเป็นคีย์อื่น **ห้ามลบทั้งSilver Lining Studio, Software หรือHKEY_CURRENT_USER** ไม่ลบค่าอื่นตามการเดา
3. ปิดRegistry Editor ผู้ใช้เปิดSteamและเกมVanillaเองหนึ่งครั้ง ให้เกมสร้างค่าใหม่ แล้วบันทึกว่าเข้าเมนูได้หรือยัง ไม่ลงBepInEx/มอดระหว่างทดสอบนี้
4. ถ้ายังดำ ให้หยุดและรายงาน ไม่ลบคีย์ซ้ำไปเรื่อย ๆ หรือกู้Save/Cloudเพื่อบังคับให้ผ่าน ไม่ยืนยันว่าEpicจะหายตามSteam

**อย่าImportไฟล์สำรองเดิมกลับทันที** หากข้อมูลเดิมทำให้เกิดปัญหา การคืนค่านั้นอาจนำปัญหากลับมา เก็บไว้เปรียบเทียบ/ย้อนกลับเมื่อเข้าใจผลเท่านั้น ใช้เฉพาะBackupของเครื่องและบัญชีWindowsตนเอง **ห้ามImportRegistryBackupของTA Fontหรือผู้เล่นอื่น** และไม่มี.reg/.batสำหรับลบอัตโนมัติให้ดาวน์โหลดจากคู่มือนี้

## หลังSteamเปิดได้

ตรวจVanillaให้เข้าเมนูได้และปิดเกม แล้วค่อยทำ [ติดตั้งBepInEx→ตรวจแยก→มอดไทย](INSTALL_TH.md) อย่ารีเซตRegistryอีกรอบเพียงเพราะกำลังลงมอด ส่วนEpicหลังแก้Registryยังรอผลทดสอบใหม่ ไม่ใช่แพลตฟอร์มที่รับรอง

แหล่งข้อมูล: [Microsoft Export/Import](https://support.microsoft.com/en-us/windows/experience/backup-recovery/how-to-back-up-and-restore-the-registry-in-windows) · [Unity2019.4 PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity persistentDataPath](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) · [Steam Verify](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB/)
