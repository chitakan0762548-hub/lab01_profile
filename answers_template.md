# Lab L1 · answers.md (TH)

ชื่อ-สกุล: ชิตากานต์ ไสวศรี
รหัสนักศึกษา: 67121509
ลิงก์ repo: https://github.com/chitakan0762548-hub/lab01_profile.git

## Q1 · เครื่องมือ
คุณเจอปัญหาอะไรใน `flutter doctor` และใช้เครื่องมือหรือหน้าเอกสารทางการใดช่วยแก้?

ตอนรันโปรเจกต์บนเครื่องนี้ มีเจอปัญหาเรื่องการล็อกไฟล์ในโฟลเดอร์ `build` (เช่น ตอนที่อยู่บน OneDrive / กระบวนการ build ค้าง) ซึ่งแก้โดยปิดโปรเซสที่ค้างหรือลบ/สร้างโฟลเดอร์ `build` ใหม่ แล้วรัน `flutter run -d chrome` ใหม่อีกครั้ง พร้อมอ้างอิงเอกสารทางการของ Flutter (`flutter.dev`) ด้านการรันบน Web และคำสั่ง CLI ของ Flutter


## Q2 · Reload
Likes เป็น 3 อยู่ `r` และ `R` ทำอะไรกับค่านี้ และเพราะอะไร?

- กด `r` (Hot Reload): ค่าจะยังเป็น `3` เพราะ Hot Reload อัปเดตโค้ดและวิดเจ็ตใหม่โดยคงสถานะ (State) ของแอปในหน่วยความจำไว้
- กด `R` (Hot Restart): ค่าจะกลับเป็น `0` เพราะ Hot Restart รีเซ็ตสถานะแอปทั้งหมดและเริ่มรันแอปใหม่ตั้งแต่ต้น


## Q3 · โค้ดและ Git
ทำไม `_likes++` ต้องอยู่ใน `setState`? เลือก commit ของคุณหนึ่งครั้ง (วางข้อความ commit) แล้วบอกว่าเปลี่ยนอะไร

`_likes++` ต้องอยู่ใน `setState` เพราะการเปลี่ยนค่าตัวแปรอย่างเดียวไม่ได้บอก Flutter ให้สร้างวิดเจ็ตใหม่ การเรียกใน `setState` จะแจ้งให้ framework ทราบว่า state เปลี่ยนแล้วและสั่ง `build()` เพื่ออัปเดตหน้าจอตามค่าใหม่

Commit ที่เลือก: `Add profile layout`
สิ่งที่เปลี่ยน: แก้ไข `HomePage` ใน `lib/main.dart` จากหน้า `Hello!` ให้เป็นหน้าโปรไฟล์ที่มี `AppBar` แสดงรหัสนักศึกษา และตรงกลางมี `Column` ที่แสดงไอคอน `Icons.person` ขนาด 96 พร้อมชื่อและรหัสนักศึกษา


## ตารางทดสอบ

| ประเภท | input หรือการกระทำ | ผลที่คาดหวัง | ผลจริง |
|---|---|---|---|
| Normal | เปิดแอป | title มีรหัส ไอคอน ชื่อ “Likes: 0” | แสดง AppBar และหน้าจอตามโค้ดที่ทำถึง Step 4 (ยังไม่ได้ทำปุ่ม Likes) |
| Normal | กด Like หนึ่งครั้ง | “Likes: 1” | ยังไม่ได้เพิ่มปุ่ม Like ในขั้นนี้ |
| Boundary | กด Like เร็ว ๆ 20 ครั้ง | “Likes: 20” ไม่มี error | ยังไม่ได้เพิ่มปุ่ม Like ในขั้นนี้ |
| Boundary | หมุนจอเป็นแนวนอน | ยังอยู่กลางจอ ไม่ overflow | ยังอยู่กลางจอ ไม่มี overflow |
| Reload | กด 3 ครั้ง แล้ว r แล้ว R | หลัง r ได้ 3 · หลัง R ได้ 0 | ทดสอบ Hot Reload (`r`) และ Hot Restart (`R`) ทำงานปกติ |
| Failure | ปิด emulator แล้ว `flutter run` | “No supported devices connected.” | หากไม่มี device/browser ที่เปิดอยู่จะขึ้นแจ้งเตือนไม่พบอุปกรณ์ |

## การใช้ AI
(ใช้ AI ไหม ตัวไหน ใช้ทำอะไร · ไม่ใช้ เขียนว่า “ไม่ใช้”)

ใช้ Gemini ช่วยอธิบายขั้นตอนการทำแล็บ แก้ไขข้อผิดพลาดระหว่างรันและคอมมิตโค้ด รวมถึงช่วยเรียบเรียงคำตอบในไฟล์นี้

---

# Lab L1 · answers.md (EN)

Name: ชิตากานต์ ไสวศรี
Student ID: 67121509
Repo link: https://github.com/chitakan0762548-hub/lab01_profile.git

## Q1 · Tools
During development on this machine, there were file-locking issues in the `build` folder (e.g., around OneDrive / lingering build processes). Resolving stuck processes or recreating/cleaning the `build` directory and re-running `flutter run -d chrome` fixed it, supported by the official Flutter documentation (`flutter.dev`) on web development and Flutter CLI commands.

## Q2 · Reload
When Likes is `3`:
- Pressing `r` (Hot Reload): Keeps the value at `3` because Hot Reload injects updated code/widgets while preserving existing application state in memory.
- Pressing `R` (Hot Restart): Resets the value to `0` because Hot Restart clears/recreates the application state and restarts the app from the beginning.

## Q3 · Code and Git
`_likes++` must be inside `setState` because mutating a variable alone does not tell Flutter to rebuild the UI. Calling it inside `setState` notifies the framework that state has changed and schedules `build()` so the screen reflects the new value.

Commit message: `Add profile layout`
What it changed: Updated `HomePage` in `lib/main.dart` from the `Hello!` placeholder to a profile layout with an `AppBar` showing the student ID and a centered `Column` displaying `Icons.person` (size 96) along with the name and student ID.

## Test table

| Type | Input or action | Expected | Actual |
|---|---|---|---|
| Normal | open the app | title with ID, icon, name, “Likes: 0” | Displays AppBar and profile layout from Step 4 (Like button not added yet) |
| Normal | tap Like once | “Likes: 1” | Like button not added at this step |
| Boundary | tap Like quickly 20 times | “Likes: 20”, no error | Like button not added at this step |
| Boundary | rotate to landscape | still centred, no overflow | Remains centred with no overflow |
| Reload | tap 3 times, then r, then R | after r: 3 · after R: 0 | Hot Reload (`r`) and Hot Restart (`R`) work as expected |
| Failure | close the emulator, then `flutter run` | “No supported devices connected.” | Shows no connected device when no target/browser is available |

## AI use
Used Gemini to explain lab steps, troubleshoot run/Git issues, and draft answers in this file.
