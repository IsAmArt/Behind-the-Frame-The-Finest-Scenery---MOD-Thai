# ปัญหาที่ทราบ / Known Issues

[หน้าแรก](README.md) · [English README](README_EN.md)

**Full Content — Public Pre-release** · เนื้อหาไทยครบ แต่ยังไม่รับรอง QA ในเกมของแพ็กนี้ครบทุกจุด / Exact-package gameplay QA is incomplete.

## กลับเมนูแล้วเลือกเล่นบทเดิม: อาจจอดำ

หากออกจากบทที่กำลังเล่นกลับไปหน้าเมนู แล้วเลือกเข้าเล่นบทเดิมอีกครั้งโดยยังไม่ปิดเกม บางครั้งหน้าจอจะแสดงหมายเลขบทตามปกติ แต่เมื่อกำลังเข้าสู่ฉากเล่น ภาพอาจกลายเป็นสีดำ แม้ว่ายังได้ยินเสียงเกมอยู่ เมาส์หรือปุ่มควบคุมยังอาจตอบสนอง

อาการนี้เกิด **หลังหน้าหมายเลขบท เมื่อควรเห็นฉากเกม** ไม่ใช่พื้นดำปกติของหน้า Loading หรือหน้าหมายเลขบท

หากพบ ให้ลองปิดเกมแล้วเปิดใหม่ก่อนเข้าเล่นอีกครั้ง วิธีนี้อาจช่วยได้ แต่ยังไม่รับประกันว่าจะสำเร็จทุกกรณี ปัญหานี้เคยเกิดในการทดสอบที่ไม่ได้เปิดใช้มอดไทย และในการทดสอบที่ปิดเส้นทางโหลด BepInEx แล้วด้วย ยังไม่ทราบสาเหตุแน่ชัด ไม่สรุปว่าเป็นความผิดของมอดหรือเกมต้นฉบับ และไม่ได้รับการแก้ไขในชุดนี้

การเลือกบทอื่นคั่นแล้วกลับมา (A→B→A) เคยแสดงภาพปกติในการทดสอบ แต่ไม่ใช่วิธีแก้ที่รับรอง ไม่แนะนำให้แก้เซฟหรือล้างข้อมูลเพื่อฝืนทดสอบ

## กด ESC ครั้งแรกแล้วหน้าต่างแว๊บหาย

หน้าต่างยืนยันกลับเมนูอาจเปิดแล้วหายทันทีเมื่อกด ESC ครั้งแรก ในผลที่สังเกต ครั้งถัดไปเปิดได้ตามปกติ อาการนี้เกิดขณะภาพเกมปกติได้ด้วย เป็นคนละประเด็นกับจอดำ ยังไม่อ้างว่าแก้แล้ว

## บท6 / เล่นต่อ (Continue)

เคยมีรายงานเส้นทางเลือกบท → ESC → กลับเมนู → เล่นต่อผิดปกติ พร้อมข้อผิดพลาด PuzzleJackSign ครั้งแรกและ PaintCraft ภายหลัง ยังไม่ยืนยันกับ ZIP ใหม่นี้ ไม่ได้หมายความว่าทุกคนจะเจอหรือมีสาเหตุเดียวกับจอดำ หากพบให้หยุดเส้นทางนั้นและแจ้งผล ไม่รีเซต/กู้ทับเซฟ

## ขอบเขตที่เคยทดสอบ

Steam / Windows x64 / Unity IL2CPP2019.4.18f1 / BepInEx6.0.0-be.788 / plugin0.7.21 เป็นชุดที่เคยทดสอบ แพ็กเผยแพร่ชุดนี้ยังรอ QA เฉพาะชุด ป้าย v2.0.4_01 ในภาพเก่าไม่ใช่การยืนยัน Steam BuildID ทุกชุด

**Epic: NOT SUPPORTED / NOT VALIDATED** — ผู้ใช้รายงานว่าเกม Epic เดิมยังเปิดไม่ได้ในการทดสอบล่าสุด จึงไม่มีผล QA มอดบน Epic ไม่อนุมานสาเหตุหรือความเข้ากันได้จากเกม Steam ไม่รับรอง GOG, Linux, macOS, Proton, Steam Deck, VR หรือ build อื่น การสลับภาษากลาง Cinema ยังไม่ผ่าน QA

## English

### Black screen after selecting the same chapter again

After leaving a chapter for the main menu, selecting that same chapter again without closing the game can show its chapter number normally, then turn black **when gameplay should appear**. Audio and mouse/input may continue. This is not the ordinary black Loading or chapter-number screen.

Try closing and reopening the game before entering again; it may help but is not guaranteed. The symptom also occurred in controls without the Thai plugin and with the verified BepInEx loading route disabled. The cause is **UNKNOWN**; neither the mod nor the original game is assigned blame, and no fix is claimed here. A→B→A worked in user tests but is not guaranteed. Never change/reset saves to force a test.

### First ESC popup flashes and disappears

The first press may open/dismiss the return-home prompt briefly; the next press worked in observed tests. It also occurred during visible gameplay and is separate from the black-screen issue. No fix is claimed.

### Chapter6 / Continue

Historical chapter-selection/ESC/Home/Continue failures included a first PuzzleJackSign exception followed by PaintCraft errors. They remain open/not reconfirmed against this ZIP. This does not mean everyone encounters them or that they share the black-screen cause. Stop a failing route and report it; do not reset/restore saves.

### Compatibility and QA

Historically tested: Steam Windows x64, Unity IL2CPP2019.4.18f1, BepInEx6.0.0-be.788, plugin0.7.21. This public ZIP still needs exact-package user QA. Old screenshot labels are not a verified Steam BuildID. **Epic is NOT SUPPORTED / NOT VALIDATED**: the user reports the unmodified Epic game did not launch in the latest test, so no mod QA is available there. Do not infer a cause or support from Steam results. Other stores, OSes, VR/builds and mid-Cinema language changes are untested.

SAME_CHAPTER_REENTRY=OPEN_USER_REPRODUCED · ROOT_CAUSE=UNKNOWN
