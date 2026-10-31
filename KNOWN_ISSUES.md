# ปัญหาที่ทราบ / Known Issues

[หน้าแรก](README.md) · [English README](README_EN.md)

**Full Content — Public Pre-release** · เนื้อหาไทยครบ แต่ยังไม่รับรอง QA ในเกมของแพ็กนี้ครบทุกจุด / Exact-package gameplay QA is incomplete.

## A. จอดำตั้งแต่เปิดเกม — คนละเรื่องกับเข้าบทเดิมซ้ำ

ผู้จัดทำเคยพบSteam Vanillaดำก่อนเข้าเมนู หลังแก้Registryของเกมเปิดได้ ค่าต้นเหตุยังUNKNOWN ส่วนEpic Vanillaเปิดได้หลังเปลี่ยนชื่อโฟลเดอร์ข้อมูลเก่าในLocalLow (สำรองไว้ก่อน) ตอนนี้ **ทดสอบใช้งานเบื้องต้นสำเร็จทั้ง Steam และ Epic Games Store บน Windows x64 โดยผู้จัดทำ** ไม่ใช่การยืนยันroot causeหรือแก้ได้ทุกเครื่อง [แนวทางสำรอง/ตรวจstartup](docs/STARTUP_BLACK_SCREEN_TH.md) ไม่ทำRegistryresetและLocalLowrenameพร้อมกันเป็นค่าเริ่มต้น

## C. คัตซีนไม่เล่น — Video Codec

บางเครื่องอาจลองเปลี่ยนSettingsจากH.264เป็นVP8ตาม [ผู้จัดจำหน่าย8กรกฎาคม2022](https://steamcommunity.com/games/1634150/announcements/detail/3335495035148049868) โดยประกาศกล่าวถึงSteamDeckด้วย [คำอธิบายและขอบเขต](docs/TROUBLESHOOTING_TH.md#video-codec) ไม่ใช่วิธีที่ยืนยันว่าแก้Aหรืออาการเข้าบทเดิมซ้ำด้านล่าง และไม่รับรองมอดบนSteamDeck

**English — A and C are separate:** Steam recovered after owner Registry edits (value unknown); Epic recovered after renaming old LocalLow game data with backup. Both stores now passed owner basic runtime testing, not exhaustive QA. [Startup recovery](docs/STARTUP_BLACK_SCREEN_EN.md). For affected cutscene playback, the publisher suggested H.264→VP8, mentioning SteamDeck; [codec guidance](docs/TROUBLESHOOTING_EN.md#video-codec) is not a confirmed startup or same-chapter fix.

## กลับเมนูแล้วเลือกเล่นบทเดิม: อาจจอดำ

หากออกจากบทที่กำลังเล่นกลับไปหน้าเมนู แล้วเลือกเข้าเล่นบทเดิมอีกครั้งโดยยังไม่ปิดเกม บางครั้งหน้าจอจะแสดงหมายเลขบทตามปกติ แต่เมื่อกำลังเข้าสู่ฉากเล่น ภาพอาจกลายเป็นสีดำ แม้ว่ายังได้ยินเสียงเกมอยู่ เมาส์หรือปุ่มควบคุมยังอาจตอบสนอง

อาการนี้เกิด **หลังหน้าหมายเลขบท เมื่อควรเห็นฉากเกม** ไม่ใช่พื้นดำปกติของหน้า Loading หรือหน้าหมายเลขบท

หากพบ ให้ลองปิดเกมแล้วเปิดใหม่ก่อนเข้าเล่นอีกครั้ง วิธีนี้อาจช่วยได้ แต่ยังไม่รับประกันว่าจะสำเร็จทุกกรณี ปัญหานี้เคยเกิดในการทดสอบที่ไม่ได้เปิดใช้มอดไทย และในการทดสอบที่ปิดเส้นทางโหลด BepInEx แล้วด้วย ยังไม่ทราบสาเหตุแน่ชัด ไม่สรุปว่าเป็นความผิดของมอดหรือเกมต้นฉบับ และไม่ได้รับการแก้ไขในชุดนี้

การเลือกบทอื่นคั่นแล้วกลับมา (A→B→A) เคยแสดงภาพปกติในการทดสอบ แต่ไม่ใช่วิธีแก้ที่รับรอง ไม่แนะนำให้แก้เซฟหรือล้างข้อมูลเพื่อฝืนทดสอบ

## กด ESC ครั้งแรกแล้วหน้าต่างแว๊บหาย

หน้าต่างยืนยันกลับเมนูอาจเปิดแล้วหายทันทีเมื่อกด ESC ครั้งแรก ในผลที่สังเกต ครั้งถัดไปเปิดได้ตามปกติ อาการนี้เกิดขณะภาพเกมปกติได้ด้วย เป็นคนละประเด็นกับจอดำ ยังไม่อ้างว่าแก้แล้ว

## บท6 / เล่นต่อ (Continue)

เคยมีรายงานเส้นทางเลือกบท → ESC → กลับเมนู → เล่นต่อผิดปกติ พร้อมข้อผิดพลาด PuzzleJackSign ครั้งแรกและ PaintCraft ภายหลัง ยังไม่ยืนยันกับ ZIP ใหม่นี้ ไม่ได้หมายความว่าทุกคนจะเจอหรือมีสาเหตุเดียวกับจอดำ หากพบให้หยุดเส้นทางนั้นและแจ้งผล ไม่รีเซต/กู้ทับเซฟ

## ขอบเขตที่ทดสอบ

**ทดสอบใช้งานเบื้องต้นสำเร็จทั้ง Steam และ Epic Games Store บน Windows x64 โดยผู้จัดทำ** (31ตุลาคม2026): Vanilla, BepInEx6.0.0-be.788และไทยทำงานได้ตามผลผู้จัดทำ ไม่ใช่การตรวจครบทุกบท/build หรือStablecertification ไม่สรุปว่าbinaryสองร้านเหมือนกัน SteamเคยตรวจUnity IL2CPP2019.4.18f1;ข้อมูลนั้นไม่แทนbuildEpic ไม่รับรองร้านอื่น Linux/macOS/Proton/SteamDeck/VRหรือการสลับภาษากลางCinema ป้ายv2.0.4_01ในภาพไม่ใช่SteamBuildID

## English

### Black screen after selecting the same chapter again

After leaving a chapter for the main menu, selecting that same chapter again without closing the game can show its chapter number normally, then turn black **when gameplay should appear**. Audio and mouse/input may continue. This is not the ordinary black Loading or chapter-number screen.

Try closing and reopening the game before entering again; it may help but is not guaranteed. The symptom also occurred in controls without the Thai plugin and with the verified BepInEx loading route disabled. The cause is **UNKNOWN**; neither the mod nor the original game is assigned blame, and no fix is claimed here. A→B→A worked in user tests but is not guaranteed. Never change/reset saves to force a test.

### First ESC popup flashes and disappears

The first press may open/dismiss the return-home prompt briefly; the next press worked in observed tests. It also occurred during visible gameplay and is separate from the black-screen issue. No fix is claimed.

### Chapter6 / Continue

Historical chapter-selection/ESC/Home/Continue failures included a first PuzzleJackSign exception followed by PaintCraft errors. They remain open/not reconfirmed against this ZIP. This does not mean everyone encounters them or that they share the black-screen cause. Stop a failing route and report it; do not reset/restore saves.

### Compatibility and QA

Basic runtime testing succeeded on both Steam and Epic Games Store on Windows x64, confirmed by the project owner on31October2026. Vanilla, pinned BepInEx and Thai selection/use passed basic checks. This is not all-chapter/all-build regression QA, stable certification or proof of identical Steam/Epic binaries. Steam's previously inspected Unity IL2CPP2019.4.18f1 metadata does not certify Epic's build. Other stores/OSes/VR/SteamDeck and mid-Cinema locale changes remain unvalidated. Old screenshot labels are not verified build IDs.

SAME_CHAPTER_REENTRY=OPEN_USER_REPRODUCED · ROOT_CAUSE=UNKNOWN
