# Rust Tutorial Project — Principles of Programming Languages

> **กลุ่มที่:** 14
> **Topic No.:** 14
> **Topic Name:** Error Handling: Option & Result
> **ประเด็นหลักที่ควรครอบคลุม:** Option, Result, Some/None, Ok/Err, error propagation, ?

---

## 1. Members

| # | Name | Student ID | GitHub Username | Main Responsibility |
|---|---|---|---|---|
| 1 | นายกันต์ธร บุตรเบ้า | 670710619 | `@[กรอก GitHub username]` | Concept + Short Code Illustration (สรุปแนวคิดหลัก + โค้ดตัวอย่างสั้น) |
| 2 | นางสาวฉันทณัฏฐ วิชพันธุ์ | 670710620 | `@[กรอก GitHub username]` | Detailed Code + Live Demo (โค้ดเชิงลึก + สาธิตสด) |
| 3 | นางสาวณัฐกฤตา บุญมี | 670710621 | `@[กรอก GitHub username]` | Rust vs Other Language + PPL Analysis (เปรียบเทียบภาษา + วิเคราะห์เชิง PPL) |
| 4 | นายณัฐวีร์ บุญยินดี | 670710622 | `@[กรอก GitHub username]` | Exercises + Common Mistakes + Challenge (แบบฝึกหัด + ข้อผิดพลาดที่พบบ่อย + คำถามท้าทาย) |

> แก้ไข GitHub Username ของแต่ละคนให้ตรงกับบัญชีจริงก่อนเริ่มทำงาน (ผู้สอนจะใช้คอลัมน์นี้เชิญเป็น collaborator ของ repository)

---

## 2. Learning Objectives

หลังจากศึกษา Topic นี้แล้ว ผู้เรียนสามารถ:

1. `[อธิบายแนวคิดสำคัญได้]`
2. `[เขียนโปรแกรม Rust ที่เกี่ยวข้องได้]`
3. `[วิเคราะห์พฤติกรรม/กฎของภาษาได้]`
4. `[เปรียบเทียบ Rust กับภาษาอื่นได้]`

---

## 3. Introduction

`[เขียนเนื้อหาที่นี่ — ใช้โครงสร้างเดียวกับ rust_tutorial_template.md ฉบับเต็มที่ผู้สอนแจกให้]`

---

## 4. Key Concepts

### 4.1 `[Concept 1]`

**คำอธิบาย**

`[อธิบายแนวคิด]`

**ตัวอย่าง**

```rust
fn main() {
    println!("Hello, Rust!");
}
```

**Explanation**

`[อธิบายว่า code ทำงานอย่างไร]`

---

### 4.2 `[Concept 2]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.3 `[Concept 3]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.4 `[Concept 4 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.5 `[Concept 5 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

## 5. Important Syntax / Rules

| Syntax / Rule | Meaning | Example |
|---|---|---|
| `Option<T>` | `ใช้ในการแทนที่ค่า ซึงจะมีค่าหรือไม่มีค่าก็ได้` | `let x: Option<i32> = Some(10)` |
|`Some(value)`|`แสดงว่า Option มีค่า`|`Some(10)`|
|`None`|`แสดงว่า Option ไม่มีค่า`|`let x: Option<i32> = None`|
| `Result<T, E>` | `ใช้ในการแทนที่ผลลัพธ์ที่สำเร็จหรือไม่สำเร็จก็ได้` | `let result: Result<i32, Err> = Ok(10)` |
|`Ok(value)`|`แสดงว่าผลลัพธ์สำเร็จ `|`OK(10)`|
|`Err(error)`|`แสดงว่าผลลัพธ์ไม่สำเร็จ`|`Err("Invalid input"`|
|`match`|`ใช้ตอนแยกหรือจัดการแต่ละกรณีของ Option/Result`|`match result {Ok(x),Err(e),}`|
| `let value =  function()?;` | ` ถ้า Ok/Some ให้ทำงานต่อไป แต่ถ้า Err/None ให้ส่งค่ากลับจาก function ` | `let x = get_number()?;` |
|`unwrap()`|`ดึงค่าจาก Some/Ok แต่ถ้า None/Err จะเกิด  panic`|`let x = Some(10).unwrap();`|


### Important Rules

1. `Option จัดการ 2 กรณีได้แก่ Some ,None`
2. `Result จัดการ 2 กรณี ได้แก่ Ok,Err`
3. `? สำหรับ Error/ Value Propagation และ Function ต้องมี return type ที่รองรับ propagate เช่น Result , Option `
4. `unwrap สามารถทำให้ program panic ได้หากผลลัพธ์ที่ได้ Error `

---

## 6. Runnable Code Examples

> **ข้อกำหนด:** Code ทุกตัวต้อง Compile และ Run ได้จริงก่อนนำมาใส่ในเอกสาร

### Example 1 — `[Panic]`

**Purpose:** `แสดงการทำงานของ panic`

```rust
fn cause_panic(value: i32){
    if value == 0{
        panic!("Panic! The value was zero, which is not allowed here");
    }
    println!("Value{} is fine.",value);
}
fn main() {
    cause_panic(0); 
}
```
**Expected Output**

```text
Panic! The value was zero, which is not allowed here
```

**Explanation**

`ส่วนแรกเป็นการสร้าง function ขึ้นมาสำหรับเช็คค่า integer ถ้าค่าที่รับมาตรงตามเงื่อนไข if value == 0 ดังเช่น code ตัวอย่างที่เป็น function main ที่มีการส่งค่า 0 เข้าไปใน function cause_panic ทำให้ output เกิด panic `

---

### Example 2 — `[Option]`

**Purpose:** `แสดงการใช้งานของ option `

```rust
fn find_first_a(text: &str) -> Option<usize>{
    text.find('a') 
}
fn main() {
    match find_first_a("Hello World!"){
        Some(index) => println!("The first 'a' is at index {}", index),
        None => println!("No 'a' found in the text."),
    }
}
```
**Expected Output**

```text
No 'a' found in the text.
```

**Explanation**

`อันดับแรกก็จะทำการสร้าง function ในการหาตัว a ตัวแรกโดยให้มี return type เป็น option จากนั้นใน main เราก็ทำการสร้าง match ขึ้นมาเพื่อทำการเช็คข้อความที่ใส่เข้าไปในฟังก์ชัน ซึ่งข้อความตามตัวอย่างจะไม่มีตัว a เลย ทำให้ได้ None แทน ดังนั้นข้อความที่ได้จึงเป็น No 'a' found in the text. `

---

### Example 3 — `[Result]`

**Purpose:** `แสดงการทำงานของ result`

```rust
#[derive(Debug)]
struct DivisionError{
    message: String,
}
fn divide(numerator: f64, denominator: f64) -> Result<f64, DivisionError>{
    if denominator == 0.0 {
        Err(DivisionError{
            message: "Cannot divide by Zero ".to_string(),
        })
    }else {
        Ok(numerator / denominator)
    }
}
fn main() {
    println!("{:?}",divide(5.0,2.0));
    println!("{:?}",divide(5.0,0.0));
}
```

**Expected Output**

```text
Ok(2.5)
Err(DivisionError { message: "Cannot divide by Zero " })
```

**Explanation**

`ขั้นตอนแรกเราก็จะสร้าง ประเภทของ DivisionError สำหรับเป็นประเภท error จากนั้นสร้างfunction divide ที่มี return เป็น Result และรับพารามิเตอร์ 2 ตัว เป็น float ทั้งคู่ โดยในฟังก์ชันจะมีเงื่อนไขหาก denominator ที่รับมาเป็น 0.0 จะได้ error ซึ่ง error คือตัว DivisionError ที่เราสร้างไว้ตอนแรก และทำการระบุข้อความที่เราต้องการให้ขึ้นเมื่อตัวหารที่เราใส่เป็น 0.0 ดังตัวอย่างในส่วนของ main ที่เราเรียกใช้ค่าที่ตัวหารเป็น 2.0 และ 0.0  `

---
### Example 4 — `[Unwrap]`

**Purpose:** `การใ้ช unwrap`

```rust
fn main(){
    let f = File::open("hello.txt").unwrap();
} 
```

**Expected Output**

```text
called `Result::unwrap()` on an `Err` value: Os { code: 2, kind: NotFound, message: "No such file or directory" }
```

**Explanation**

`unwrap ทำงานเหมือน match ซึ่งค่า f จะมี data type เป็น file โดย unwrap สามารถเป็นค่าสำเร็จ (Ok()) หรือ ไม่สำเร็จ(Err)ได้ กรณีไม่สำเร็จจะเกิด panic จาก code ตัวอย่างจะได้ output Err เนื่องจากไม่พบไฟล์ hello.txt `

---
### Example 5 — `[Expect]`

**Purpose:** `แสดงการใช้งาน expect`

```rust
fn main(){
     let f = File::open("hello.txt").expect("Failed to open it ");
} 
```

**Expected Output**

```text
Failed to open it : Os { code: 2, kind: NotFound, message: "No such file or directory" }
```

**Explanation**

`การใช้ expect สามารถระบุข้อความที่เราต้องการลงไปได้ในกรณีที่ Error แล้ว`

---
### Example 6 — `[Error Propagation]`

**Purpose:** `--`

```rust
fn read_username_from_file() -> Result<String, io::Error>{
    let f = File::open("hello.txt"); 

    let mut f = match f {
        Ok(file) => file, 
        Err(e) => return Err(e),
    };

    let mut s = String::new();

    match f.read_to_string(&mut s){
        Ok(_) => Ok(s),
        Err(e) => Err(e),
    }
}
fn main(){
    ...
} 
```

**Expected Output**

```text
[]
```

**Explanation**

`[]`

---
### Example 7 — `[? Operator]`

**Purpose:** `แสดงการใช้ ?`

```rust
fn calculate_division_then_add_one(num: f64, den: f64)->Result<f64,DivisionError>{
    let result = divide(num, den)?;
    Ok(result +1.0)
}
fn main(){
    println!("{:?}", calculate_division_then_add_one(5.0,2.0));
    println!("{:?}", calculate_division_then_add_one(5.0,0.0));
}
```

**Expected Output**

```text
Ok(3.5)
Err(DivisionError { message: "Cannot divide by Zero " })
```

**Explanation**

`ส่วนแรกก็จะเป็น function สำหรับการหารก่อนจะบวกเพิ่ม 1.0 โดยเราจะใช้ ? แทนการเขียน match ซึึ่งถ้าบรรทัดที่่ 2 สามารถคำนวนการหารผ่านได้ บรรทัดด่อมาที่เป็น Ok ก็จะทำงานต่อ แต่ถ้า Error บรรทัด Ok ก็จะไม่ถูกทำงาน  `

---

## 7. Common Mistakes

### Mistake 1 — `[Using .unwrap() in production code.]`

**Problem**

`การใช้ production code นั้นถ้าใช้ .unwrap() แล้วเจอ Err จะทำให้ thread นั้นเกิดการ panic ซึ่งถ้าการ panic เกิดขึ้นที่ web server จะทำให้การจัดการคำขอ(Request Handling)หยุดทำงาน และ หากเกิดข้อผิดพลาดร้ายแรงในงานแบบ asynchronous อาจทำให้งานหยุดทำงานโดยไม่แจ้งให้ทราบล่วงหน้า`

**Incorrect Code**

```rust
use std::fs;

fn main() {
    let contents = fs::read_to_string("config.txt").unwrap();
    let port: u16 = contents.trim().parse().unwrap();

    println!("Starting server on port {}", port);
}
```

**Correct Code**

```rust
use std::error::Error;
use std::fs;

fn main() -> Result<(), Box<dyn Error>> {
    let contents = fs::read_to_string("config.txt")?;
    let port: u16 = contents.trim().parse()?;

    println!("Starting server on port {}", port);
    Ok(())
}
```

**Why?**

`เพราะ .unwrap() ตรวจเจอข้อผิดพลาดแล้ว panic จะทำการ crash โปรแกรม แต่ถ้าเราใช้ ? แทนนั้น Err จะถูกส่งกลับไปให้ caller เลือกวิธีจัดการ`

---

### Mistake 2 — `[Matching on error strings instead of error variants.]`

**Problem**

`มือใหม่มักเช็กข้อผิดพลาดด้วยการดูข้อความ เช่น err.contains("not found") ซึ่งเปราะบางมาก เพราะข้อความ error เปลี่ยนได้ทุกเมื่อ เช่น แก้คำ แก้ภาษา หรือเปลี่ยนรูปแบบ พอข้อความเปลี่ยน โค้ดยังคอมไพล์ผ่านตามปกติ แต่เงื่อนไขที่เช็กไว้จะไม่ทำงานอีกต่อไปโดยไม่มีอะไรเตือนเลย`

**Incorrect Code**

```rust
fn find_user(id: u32) -> Result<String, String> {
    if id == 1 {
        Ok("Alice".to_string())
    } else {
        Err("user not found".to_string())
    }
}

fn main() {
    match find_user(2) {
        Ok(name) => println!("Hello {}", name),
        Err(err) => {
            if err.contains("not found") {
                println!("Creating a new user...");
            } else {
                println!("Something else went wrong");
            }
        }
    }
}
```

**Correct Code**

```rust
#[derive(Debug)]
enum AppError {
    UserNotFound,
    DatabaseDown,
}

fn find_user(id: u32) -> Result<String, AppError> {
    if id == 1 {
        Ok("Alice".to_string())
    } else {
        Err(AppError::UserNotFound)
    }
}

fn main() {
    match find_user(2) {
        Ok(name) => println!("Hello {}", name),
        Err(AppError::UserNotFound) => println!("Creating a new user..."),
        Err(AppError::DatabaseDown) => println!("Try again later"),
    }
}
```

**Why?**

`การเช็ก error ด้วย String ทำให้โค้ดต้องไปพึ่งข้อความที่เขียนไว้ ซึ่งคอมไพเลอร์ไม่ได้ช่วยตรวจสอบตรงนี้ ถ้ามีการเปลี่ยนข้อความจาก user not found เป็น no such user โค้ดที่ใช้ตรวจจับ error ก็อาจไม่ทำงานโดยที่เราไม่รู้ตัว แต่ถ้าใช้ enum เราสามารถกำหนดประเภทของ error ไว้ชัดเจน ทำให้ Rust สามารถตรวจสอบผ่านระบบ type ได้
`

---

## 8. Exercises

> จัดทำแบบฝึกหัด **2 ข้อ** ที่สอดคล้องกับ Topic และมีระดับความยากเหมาะสม

### Exercise 1 — `[ชื่อโจทย์]`

**Problem**

`[เขียนโจทย์]`

**Hint**

`[คำใบ้]`

**Solution**

```rust
// Solution code
```

**Explanation**

`[อธิบายแนวทางแก้]`

---

### Exercise 2 — `[ชื่อโจทย์]`

**Problem**

`[เขียนโจทย์]`

**Hint**

`[คำใบ้]`

**Solution**

```rust
// Solution code
```

**Explanation**

`[อธิบายแนวทางแก้]`

---

## 9. PPL Perspective


### 9.1 Syntax

&emsp; ภาษา Rust ใช้แนวคิดการคืนค่าผลลัพธ์ (Return Values) ในการจัดการข้อผิดพลาดผ่านชนิดข้อมูล `Option` และ `Result` โดยไม่มีการใช้โครงสร้างไวยากรณ์เฉพาะสำหรับการโยน Exception (เช่น คีย์เวิร์ด `try`, `catch`, `throw`) แต่ประยุกต์ใช้โครงสร้างไวยากรณ์พื้นฐานร่วมกับกลไก Pattern Matching และ `?` operator ดังนี้

- **การนิยามโครงสร้างข้อมูลด้วย Enum และ Generic Parameters (`<T, E>`)**

  โดยใช้ไวยากรณ์ Enum ร่วมกับ Generic Parameters (`<T, E>`) เพื่อสร้างประเภทข้อมูลที่ยืดหยุ่น รองรับข้อมูลชนิดใดก็ได้ สำหรับใช้แทนกรณีการทำงานที่สำเร็จและกรณีที่เกิดข้อผิดพลาด

- **การควบคุมทิศทางโปรแกรมด้วย Pattern Matching**

  โดยใช้ไวยากรณ์ `match` และ `if let` เป็นโครงสร้างหลักในการควบคุมทิศทางโปรแกรม ตรวจสอบกรณีที่เกิดข้อผิดพลาด และแกะค่าข้อมูลออกจาก `Option` และ `Result`

- **การจัดการและส่งต่อข้อผิดพลาดด้วย `?` Operator**

  โดยใช้เครื่องหมาย `?` เพื่อลดรูปโค้ดการตรวจสอบ `Result` หรือ `Option` แทนการเขียนคำสั่ง `match` ที่ยาว โดยทำงานแบบ Short-circuiting ซึ่งจะส่งคืนข้อผิดพลาดกลับไปยังฟังก์ชันที่เรียกใช้งานทันทีโดยอัตโนมัติ

- **การดึงข้อมูลด้วย `unwrap()` และ `expect()`**

  เป็นเมธอดสำหรับดึงค่าข้อมูลข้างในของ `Option` และ `Result` ออกมาใช้งาน โดยจะทำให้โปรแกรมหยุดทำงานทันที หรือเรียกว่า panic ถ้าค่าที่ได้ไม่ใช่ค่าที่ประมวลผลสำเร็จ หรือเป็นค่า `None`/`Err`

  `expect()` จะแตกต่างกับ `unwrap()` ตรงที่สามารถระบุข้อความอธิบายสาเหตุของการหยุดทำงานเพิ่มเติมได้

- **การสั่งหยุดโปรแกรมด้วยคำสั่ง `panic!`**

  เป็นคำสั่งที่ใช้สั่งหยุดการทำงานของโปรแกรมทันที เมื่อเจอข้อผิดพลาดร้ายแรงจนไม่สามารถประมวลผลต่อหรือกู้คืนได้ เช่น การหารด้วยศูนย์ (Division by Zero), การเข้าถึงข้อมูลเกินขอบเขตของอาร์เรย์ (Index Out of Bounds)


### 9.2 Semantics

- **การมอง Error เป็นค่าข้อมูลทั่วไป** นั่นคือ ภาษา Rust มองว่าข้อผิดพลาดคือค่าข้อมูลธรรมดาตัวหนึ่งที่ส่งกลับมาจากฟังก์ชันผ่าน `Result<T, E>` เหมือนกับการคืนค่าข้อมูลปกติทั่วไป ซึ่งต่างจากระบบ Exception ในภาษาอื่นตรงที่ไม่เกิดการกระโดดข้ามลำดับการทำงานโดยไม่ตั้งใจ

- **การหยุดทำงานทันทีเมื่อเจอ Error ด้วย ? Operator หรือเรียกว่า Short-Circuiting** นั่นคือ `? Operator`  ทำหน้าที่เช็กผลลัพธ์ขณะโปรแกรมทำงานทันที โดยกรณีสำเร็จ (`Ok` หรือ `Some`) จะแกะค่าออกมาให้เรานำไปประมวลผลต่อในบรรทัดนั้นตามปกติ กรณีล้มเหลว (`Err` หรือ `None`) จะหยุดทำงานคำสั่งที่เหลือในฟังก์ชันปัจจุบันทันที แล้วส่งค่าความผิดพลาดนั้นกลับไปให้ผู้เรียกใช้งาน

- **เมื่อเกิด `panic!`** ระบบรันไทม์จะเปลี่ยนจากการส่งคืนค่าตามปกติไปเป็นการสั่งให้หน่วยการทำงานปัจจุบันหยุดทำงานทันที และเริ่มกระบวนการถอยย้อน Stack เพื่อทำลายตัวแปรและคืนทรัพยากร ก่อนปิดการทำงานลง

### 9.3 Type System

- **การแยกชนิดข้อมูลเพื่อขจัดปัญหา Null** นั่นคือ ระบบ Type ของภาษา Rust ทำการแยกความแตกต่างระหว่าง `T` (ชนิดข้อมูลที่มีค่าเสมอ) และ `Option<T>` (ชนิดข้อมูลที่อาจเป็นค่าว่าง) ออกจากกันอย่างเด็ดขาด โดยคอมไพเลอร์จะปฏิเสธการส่งค่า `Option<T>` เข้าไปยังฟังก์ชันที่ต้องการ `T` โดยตรงทันที หากยังไม่ผ่านการตรวจสอบและแกะค่า ช่วยกำจัดปัญหา Null Pointer Exception ได้อย่างเด็ดขาดตั้งแต่ขั้นตอนการคอมไพล์

- **การประยุกต์ใช้ชนิดข้อมูลผลรวม (Sum Types)** นั่นคือ ภาษา Rust นิยาม `Option<T>` และ `Result<T, E>` โดยอาศัยหลักการของ Sum Type เพื่อบังคับให้ตัวแปรอยู่ในสถานะใดสถานะหนึ่งได้เพียงรูปแบบเดียวในขณะนั้น ได้แก่ `Option<T>` มีรูปแบบที่เป็นไปได้ 2 รูปแบบคือ `Some` หรือ `None` และ `Result<T, E>` มีรูปแบบที่เป็นไปได้ 2 ทางคือ `Ok` หรือ `Err`

- **การบังคับจัดการผลลัพธ์ด้วยแอตทริบิวต์ `#[must_use]`** นั่นคือ โครงสร้าง `Option` และ `Result` ถูกกำกับด้วยแอตทริบิวต์ `#[must_use]` ซึ่งบังคับให้ผู้เขียนโปรแกรมต้องนำค่าผลลัพธ์ที่คืนมาจากฟังก์ชันไปจัดการต่อเสมอ หากมีการเรียกใช้ฟังก์ชันแล้วปล่อยทิ้งไว้โดยไม่นำไปจัดการต่อ คอมไพเลอร์จะทำการแจ้งเตือนทันทีในขั้นตอนการคอมไพล์

### 9.4 Memory / Resource Management

- **ภาษา Rust ประยุกต์ใช้ระบบ Ownership** ส่งผลให้ค่าข้อมูลที่ถูกห่อหุ้มอยู่ภายใน `Option` หรือ `Result` จะถูกคืนพื้นที่หน่วยความจำ (Deallocate) อัตโนมัติทันทีเมื่อตัวแปรนั้นหมดขอบเขตการทำงาน

- **มี Null Pointer Optimization (NPO)** ซึ่งเป็นกลไกที่คอมไพเลอร์ของ Rust ใช้ปรับแต่งโครงสร้างข้อมูลประเภท `Option<T>` ในกรณีที่ `T` เป็นตัวชี้ตำแหน่งหน่วยความจำ ให้มีขนาดเท่ากับ Pointer ปกติ โดยไม่สูญเสียพื้นที่หน่วยความจำเพิ่มเติมสำหรับเก็บสถานะ `None` หรือค่าว่าง

- **ตัวแปรประเภท Enum ใน Rust มีพฤติกรรมเป็น Value Type** โดยโครงสร้างข้อมูลจะถูกจัดเก็บ ประมวลผล และส่งผ่านบน Stack โดยตรง (ยกเว้นสมาชิกภายในจะมีการอ้างอิงไปยัง Heap)

- **เมื่อโปรแกรมเกิด `panic!`** รันไทม์ของ Rust จะไล่ทำลายตัวแปรใน Stack ออกทีละตัวโดยอัตโนมัติผ่านการทำงานของ `Drop Trait` ทำให้มั่นใจได้ว่าหน่วยความจำและทรัพยากรต่าง ๆ จะถูกคืนให้ระบบทั้งหมด

### 9.5 Abstraction / Other PPL Concepts

- **รูปแบบการเขียนโปรแกรม (Paradigm):** เป็นการผสมผสานข้อดีระหว่างการเขียนโปรแกรมแบบ Functional และการเขียนโปรแกรมแบบ Imperative เข้าด้วยกัน โดยใช้แนวคิด Errors as Values ซึ่งเป็นการมองข้อผิดพลาดเป็นค่าข้อมูลธรรมดาที่ส่งกลับจากฟังก์ชัน มาทำงานร่วมกับตัว `? Operator` ที่ทำหน้าที่ส่งคืนข้อผิดพลาดกลับทันทีเมื่อเกิดปัญหา ทำให้สามารถเขียนโค้ดเรียงลำดับขั้นตอนจากบนลงล่างได้สั้นกระชับ อ่านง่ายและตรงไปตรงมาในรูปแบบ Imperative

- **การจำแนกประเภทข้อผิดพลาด** โดย Rust แบ่งการจัดการข้อผิดพลาดออกเป็น 2 ระดับอย่างชัดเจน ได้แก่

  - **ข้อผิดพลาดที่จัดการได้ (Recoverable Errors)** เป็นข้อผิดพลาดปกติทั่วไปที่ระบบคาดการณ์ไว้อยู่แล้วว่าเกิดขึ้นได้ เช่น การหาไฟล์ไม่เจอ หรือการที่ผู้ใช้ป้อนข้อมูลผิดรูปแบบ โดย Rust จะส่งผลลัพธ์กลับมาเป็นค่าข้อมูลผ่าน `Result<T, E>` หรือ `Option<T>` เพื่อให้สามารถเขียนโปรแกรมเพื่อจัดการข้อผิดพลาดนั้นได้

  - **ข้อผิดพลาดที่จัดการไม่ได้ (Unrecoverable Errors)** เป็นข้อผิดพลาดร้ายแรงจาก Bug ของโปรแกรม เช่น การหารด้วยศูนย์ (Division by Zero), การเข้าถึงข้อมูลเกินขอบเขตของอาร์เรย์ (Index Out of Bounds) ซึ่งเป็นจุดที่ระบบทำงานผิดปกติและไม่ควรฝืนประมวลผลต่อ โดย Rust จะตัดการทำงานทันทีผ่านคำสั่ง `panic!` เพื่อป้องกันข้อมูลเสียหาย

- **การซ่อนรายละเอียดข้อมูล (Data Abstraction)** โดยภาษา Rust ซ่อนค่าข้อมูลและสถานะข้อผิดพลาดไว้ภายในโครงสร้าง `Option` หรือ `Result` โดยไม่อนุญาตให้เข้าถึงตำแหน่งหน่วยความจำโดยตรง แต่บังคับให้เข้าถึงและใช้งานผ่านอินเทอร์เฟซที่ปลอดภัยที่ภาษากำหนดไว้เท่านั้น เช่น การใช้ Pattern Matching หรือเมธอดสำหรับการแกะค่า

- **ขอบเขตการทำงานและการผูกค่าตัวแปร (Scope & Binding)** โดยการแกะค่าข้อมูลด้วยโครงสร้าง Pattern Matching ได้แก่ `match` หรือ `if let Some(data) = result` ภาษา Rust จะสร้างตัวแปรใหม่ (data) เพื่อทำ Binding กับค่าภายในทันที โดยตัวแปรนี้จะมีขอบเขตการทำงานอยู่เฉพาะภายในบล็อก `{ }` ของเงื่อนไขนั้น ๆ เท่านั้น และจะถูกทำลายทันทีเมื่อออกจากบล็อก

### 9.6 Why Rust?

### **ความปลอดภัย (Safety)**

- **กำจัดปัญหา Null Pointer Exception** นั่นคือ ภาษา Rust ไม่รองรับการกำหนดค่า null ให้กับตัวแปรทั่วไป แต่บังคับให้ใช้ `Option<T>` ในการจัดการค่าว่าง จึงช่วยกำจัดปัญหา Null Pointer Exception ได้อย่างเด็ดขาด

- **ป้องกันการเข้าถึงข้อมูลที่ไม่ปลอดภัย** โดยคอมไพเลอร์จะบังคับให้ตรวจสอบสถานะและแกะค่าออกจาก `Option` หรือ `Result` ก่อนนำข้อมูลภายใน (T) ไปใช้งานเสมอ ช่วยป้องกันการนำข้อมูลที่ไม่ถูกต้องหรือข้อผิดพลาดไปใช้โดยไม่ตั้งใจ

- **ป้องกันความผิดพลาดของระบบด้วย `panic!`** โดย Rust เลือกสั่งให้โปรแกรมหยุดทำงานทันที (`panic!`) เมื่อเกิด Bug ร้ายแรง เพื่อการันตีว่าระบบจะไม่ฝืนทำงานต่อด้วยข้อมูลที่ผิดพลาด

### **ความน่าเชื่อถือ (Reliability)**

- **การจัดการข้อผิดพลาดใน Rust ทำงานเหมือนกับการคืนค่าจากฟังก์ชันตามปกติ** ไม่มีการข้ามขั้นตอนการทำงานไปที่บล็อกอื่นแบบกะทันหัน ทำให้การทำงานเป็นไปตามลำดับจากบนลงล่าง สามารถอ่านและตรวจสอบได้ง่าย

- **ป้องกันการละเลยข้อผิดพลาดด้วย `#[must_use]`** นั่นคือ โครงสร้าง `Result` และ `Option` มี attribute `#[must_use]` กำกับไว้ หากมีการเรียกฟังก์ชันที่คืนค่าเหล่านี้โดยไม่นำผลลัพธ์ไปจัดการต่อ คอมไพเลอร์จะทำการแจ้งเตือนทันที ช่วยป้องกันไม่ให้ข้อผิดพลาดถูกมองข้ามโดยไม่ตั้งใจ

### **ประสิทธิภาพ (Performance)**

- **ไม่มี Runtime Overhead บน Heap** โดยการส่งผ่านและคืนค่า `Result` และ `Option` ทำงานผ่านการคืนค่าโครงสร้างข้อมูลแบบ Enum บน Stack Frame เหมือนกับการคืนค่าฟังก์ชันทั่วไป จึงไม่มีภาระในการจองพื้นที่หน่วยความจำแบบไดนามิก และไม่ทำให้เกิด Overhead บน Heap Memory

---

## 10. Rust vs. Other Language

<h3>ตารางที่ 1: เปรียบเทียบ Rust และ Java</h3>

<table>
<thead>
<tr>
<th>Aspect</th>
<th>Rust</th>
<th>Java</th>
</tr>
</thead>

<tbody>

<tr>
<td valign="top"><strong>Syntax</strong></td>

<td valign="top">
<ul>
<li><strong>จัดการข้อผิดพลาดด้วย <code>Option&lt;T&gt;</code> และ <code>Result&lt;T, E&gt;</code>:</strong> โดย <code>Option&lt;T&gt;</code> ใช้จัดการกรณีที่ไม่มีข้อมูล (ค่าว่าง) ส่วน <code>Result&lt;T, E&gt;</code> ใช้จัดการกรณีที่เกิดข้อผิดพลาดซึ่งสามารถแก้ไขได้</li>

<li><strong>กำหนดโครงสร้างด้วย <code>Enum</code> และ รูปแบบตัวเลือกย่อย (<code>Variant</code>)</strong> ได้แก่ <code>Some/None</code> สำหรับ <code>Option</code> และ <code>Ok/Err</code> สำหรับ <code>Result</code></li>

<li><strong>แกะค่าข้อมูลด้วย <code>Pattern Matching</code></strong> โดยใช้ไวยากรณ์ <code>match</code> และ <code>if let</code></li>

<li><strong>ส่งต่อข้อผิดพลาดอย่างรวดเร็วด้วย <code>? Operator</code></strong></li>

<li><strong>เมธอดดึงค่าข้อมูล <code>unwrap()</code> และ <code>expect()</code></strong> ใช้แกะเอาค่าข้างใน <code>Option</code> หรือ <code>Result</code> ออกมาใช้งาน หากเจอข้อผิดพลาด (<code>None/Err</code>) จะสั่งหยุดโปรแกรมทันที (<code>panic!</code>) โดย <code>expect()</code> สามารถใส่ข้อความอธิบายสาเหตุเพิ่มเติมได้</li>

<li><strong>คำสั่ง <code>panic!</code></strong> คำสั่งสั่งหยุดโปรแกรมทันที ใช้เมื่อเจอข้อผิดพลาดร้ายแรงที่ไม่สามารถแก้ไขหรือประมวลผลต่อได้</li>

<td valign="top">
<ul>
<li><strong>จัดการข้อผิดพลาดด้วยโครงสร้างบล็อก <code>try-catch-finally</code></strong> โดย <code>try:</code> เป็นบล็อกสำหรับใส่คำสั่งที่มีโอกาสเกิดข้อผิดพลาด, <code>catch:</code> เป็นบล็อกดักจับและจัดการวัตถุ <code>Exception</code> ตามลำดับชั้น <code>Polymorphism</code> (ต้องเรียงจากคลาสลูกไปคลาสแม่) และ <code>finally:</code> เป็นบล็อกที่ได้รับการประมวลผลเสมอ ไม่ว่าจะเกิด <code>Exception</code> หรือไม่ก็ตาม</li>

<li><strong>การระบุข้อผิดพลาดบนส่วนหัวเมธอด</strong> ใช้คำสั่ง <code>throws</code> เพื่อบอกว่าเมธอดนั้นมีโอกาสโยน <code>Exception</code> ออกไปให้ผู้เรียกใช้งานต้องจัดการต่อ</li>
</ul>
</td>
</tr>

<tr>
<td valign="top"><strong>Semantics / Behavior</strong></td>

<td valign="top">
<ul>
<li><strong>มอง <code>Error</code> เป็นค่าข้อมูลปกติ</strong> ที่ถูกส่งคืนจากฟังก์ชันเหมือนการคืนค่าทั่วไปผ่านโครงสร้าง <code>Result&lt;T, E&gt;</code></li>

<li><strong>ตัวดำเนินการ <code>?</code> ทำงานแบบ <code>Short-circuiting</code></strong> โดยหากประมวลผลแล้วเกิดข้อผิดพลาด ระบบจะทำการคืนค่าข้อผิดพลาดกลับไปยังฟังก์ชันผู้เรียกทันทีโดยอัตโนมัติ</li>

<li><strong>คำสั่ง <code>panic!</code></strong> จะสั่งหยุดหน่วยการทำงานปัจจุบันทันทีเมื่อเกิดข้อผิดพลาดร้ายแรง โดยระบบจะถอยย้อน <code>Stack</code> เพื่อเคลียร์ตัวแปรและคืนทรัพยากร ก่อนปิดการทำงานลง</li>
</ul>
</td>

<td valign="top">
<ul>
<li><strong>เมื่อคำสั่ง <code>throw</code> ทำงาน</strong> ระบบรันไทม์จะหยุดการประมวลผลในขอบเขต ปัจจุบันทันที และเริ่มกระบวนการถอยย้อน <code>Stack</code> โดยการยกเลิก <code>Stack Frame</code> ไล่ย้อนกลับไปตามลำดับการเรียกใช้งาน เพื่อค้นหาบล็อก <code>catch</code> ที่มีชนิดข้อมูลสอดคล้องกับวัตถุ <code>Exception</code> นั้นมาจัดการ</li>
</ul>
</td>
</tr>

<tr>
<td valign="top"><strong>Type System</strong></td>

<td valign="top">
<ul>
<li><strong>การแยกชนิดข้อมูล <code>T</code> และ <code>Option&lt;T&gt;</code></strong> โดยเป็นการแยกข้อมูลที่มีอยู่จริง (<code>T</code>) ออกจากข้อมูลที่อาจไม่มีอยู่ (<code>Option&lt;T&gt;</code>) อย่างเด็ดขาด ช่วยตัดปัญหา <code>Null Pointer Exception</code> ออกไปได้ตั้งแต่ขั้นตอนคอมไพล์</li>

<li><strong>ตัวแปรจะอยู่ในสถานะใดสถานะหนึ่งได้เพียงอย่างเดียวในขณะนั้น</strong> เช่น <code>Option</code> (<code>Some</code> หรือ <code>None</code>) และ <code>Result</code> (<code>Ok</code> หรือ <code>Err</code>)</li>

<li><strong>มีแอตทริบิวต์ <code>#[must_use]</code></strong> บังคับให้ผู้เขียนโปรแกรมต้องนำผลลัพธ์ไปจัดการต่อเสมอ หากละเลยคอมไพเลอร์จะแจ้งเตือนทันที</li>
</ul>
</td>

<td valign="top">
<ul>
<li><strong>เป็นลำดับชั้นชนิดข้อมูล</strong> โดยระบบ <code>Type</code> ใน Java มีคลาสสูงสุดคือ <code>java.lang.Throwable</code> ซึ่งถูกจำแนกออกเป็น 2 ประเภทหลักคือ <code>java.lang.Error</code> (ข้อผิดพลาดรุนแรงในระดับ JVM ที่โปรแกรมไม่ควรจัดการ) และ <code>java.lang.Exception</code> (ข้อผิดพลาดจากลอจิกหรือปัจจัยภายนอกที่โปรแกรมสามารถดักจับได้)</li>

<li><strong>มี <code>Checked Exceptions</code></strong> ซึ่งเป็น Exceptions ประเภทที่บังคับตรวจสอบหรือจัดการตอนคอมไพล์</li>

<li><strong>บล็อก <code>catch (Exception e)</code></strong> สามารถดักจับ Exception ย่อยทุกตัวที่สืบทอดมาจากคลาส <code>Exception</code> ได้ทันทีตามหลัก <code>Polymorphism</code></li>
</ul>
</td>
</tr>

<tr>
<td valign="top"><strong>Memory Management</strong></td>

<td valign="top">
<ul>
<li><strong>คืนทรัพยากรอัตโนมัติด้วยหลัก <code>Ownership</code></strong> ทันทีที่ <code>Option</code> หรือ <code>Result</code> หมดขอบเขตการทำงาน (<code>Scope</code>)</li>

<li><strong>มี <code>Null Pointer Optimization (NPO)</code></strong></li>

<li><strong>ไม่มีการสร้าง <code>Overhead</code> บน <code>Heap</code></strong> เพราะโครงสร้าง <code>Enum</code> มีพฤติกรรมเป็น <code>Value Type</code> ซึ่งข้อมูลจะถูกประมวลผลและส่งผ่านบน <code>Stack</code></li>
</ul>
</td>

<td valign="top">
<ul>
<li><strong>การใช้คำสั่ง <code>throw</code></strong> จะบังคับให้ JVM สร้างออบเจกต์ <code>Exception</code> ขึ้นบน <code>Heap Memory</code> พร้อมบันทึกลำดับขั้นตอนการเรียกใช้งานฟังก์ชัน (<code>Stack Trace</code>) ทำให้กินหน่วยความจำเพิ่มขึ้นและเกิด <code>Runtime Overhead</code></li>

<li><strong>เมื่อจัดการ <code>Exception</code> ในบล็อก <code>catch</code> เสร็จสิ้น</strong> และไม่มีการใช้งานออบเจกต์นั้นต่อ ระบบ <code>Garbage Collector (GC)</code> ของ Java จะเข้ามาล้างออบเจกต์นั้นออกจาก <code>Heap Memory</code> และคืนพื้นที่ให้อัตโนมัติ</li>
</ul>
</td>
</tr>

<tr>
<td valign="top"><strong>Safety</strong></td>

<td valign="top">
<ul>
<li><strong>การันตีความปลอดภัยตั้งแต่ขั้นตอนคอมไพล์</strong> โดยคอมไพเลอร์จะบังคับให้โปรแกรมเมอร์ต้องเขียนโค้ดรองรับทุกกรณีของข้อผิดพลาดที่อาจเกิดขึ้นขณะรันโปรแกรม (<code>Runtime</code>) ไว้ล่วงหน้าเสมอ ทำให้โปรแกรมไม่ Crash โดยไม่ได้คาดคิด</li>

<li><strong>การันตีการตรวจสอบครอบคลุมทุกกรณี</strong> โดยคอมไพเลอร์บังคับให้ต้องเขียนโค้ดรองรับทุก <code>Variant</code> ของ <code>Enum</code> (<code>Ok/Err</code> หรือ <code>Some/None</code>) ให้ครบถ้วน ป้องกันไม่ให้มีเงื่อนไขตกหล่น</li>

<li><strong>การันตีว่า Error ไม่ถูกละเลย</strong> โดยคอมไพเลอร์บังคับให้ต้องจัดการค่า <code>Result</code> ที่คืนกลับมาเสมอ ไม่สามารถเรียกฟังก์ชันแล้วปล่อยผ่านไปเฉย ๆ ได้</li>

<li><strong>ป้องกันความผิดพลาดของระบบด้วย <code>panic!</code></strong> โดยจะสั่งหยุดโปรแกรมทันทีเมื่อเกิด Bug ร้ายแรง เพื่อการันตีว่าระบบจะไม่ฝืนทำงานต่อด้วยข้อมูลที่ผิดพลาด</li>
</ul>
</td>

<td valign="top">
<ul>
<li><strong>มีความเสี่ยงที่โปรแกรมจะเกิดการทำงานผิดพลาดและล่มลงในขณะที่ทำงานอยู่</strong> ถ้าไม่ได้เขียนบล็อก <code>catch</code> ดักจับไว้ให้ครอบคลุม Error นั้น</li>

<li><strong>เสี่ยงเกิด <code>NullPointerException</code> ได้ง่าย</strong> เพราะคอมไพเลอร์บังคับตรวจจับเฉพาะ <code>Checked Exceptions</code> เท่านั้น</li>
</ul>
</td>
</tr>

</tbody>
</table>



<p><strong>หมายเหตุ:</strong> แบ่งการเปรียบเทียบออกเป็น 3 ตาราง เพื่อให้เนื้อหาไม่แน่นเกินไปและอ่านง่ายขึ้น โดยเปรียบเทียบ Rust กับ Java, Python และ Swift ตามลำดับ</p>

### Rust Example

```rust
// Rust code
```

### `[Other Language]` Example

```python
# Other language code
```

### Analysis

`[อธิบายความแตกต่างที่สำคัญ และเหตุผลด้านการออกแบบภาษา]`

---

## 11. Teach Your Topic

การนำเสนอมีสมาชิก **4 คน คนละประมาณ 5 นาที**

| Member | Responsibility | Time |
|---|---|---:|
| Member 1 | Concept + Short Code Illustration | 5 min |
| Member 2 | Detailed Code + Live Demo | 5 min |
| Member 3 | Rust vs Other Language + PPL Analysis | 5 min |
| Member 4 | Exercises + Common Mistakes + Challenge | 5 min |

### Individual Contribution

**Member 1**

`[สิ่งที่รับผิดชอบ]`

**Member 2**

`[สิ่งที่รับผิดชอบ]`

**Member 3**

`[สิ่งที่รับผิดชอบ]`

**Member 4**

`[สิ่งที่รับผิดชอบ]`

> สมาชิกทุกคนต้องสามารถอธิบาย Code ของกลุ่มได้ ไม่ใช่เฉพาะส่วนที่ตนเองเขียน

---

## 12. References

> แนะนำให้มีอย่างน้อย **4 แหล่งอ้างอิง** และควรใช้เอกสารทางการเป็นหลัก

1. `[The Rust Programming Language — Rust Book]`
2. `[Rust by Example / Rust Reference]`
3. `[Official documentation ที่เกี่ยวข้องกับ Topic]`
4. `[แหล่งอ้างอิงเพิ่มเติม]`

---

## 13. AI Usage Declaration

สามารถใช้ AI เป็นเครื่องมือช่วยเรียนรู้และพัฒนาได้ แต่สมาชิกทุกคนต้องเข้าใจและสามารถอธิบายผลงานของกลุ่มได้

| AI Tool | Purpose | How the Result Was Verified |
|---|---|---|
| `[เช่น ChatGPT]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |
| `[AI tool]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |

### Declaration

- [ ] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [ ] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [ ] ระบุการใช้ AI อย่างโปร่งใส

**รายละเอียดการใช้ AI**

`[อธิบายว่าใช้ AI ในขั้นตอนใด และสมาชิกตรวจสอบผลลัพธ์อย่างไร]`

---

## 14. GitHub Contribution

| Member | Issues | Commits | Pull Requests | Code Reviews | Contribution |
|---|---:|---:|---:|---:|---|
| Member 1 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 2 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 3 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 4 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |

### Teamwork Reflection

**How did your team collaborate?**

`[อธิบายกระบวนการทำงานร่วมกัน]`

**Problems encountered**

`[ปัญหาที่พบ]`

**How did you solve them?**

`[วิธีแก้ปัญหา]`

---

## 15. Final Checklist

- [ ] Learning Objectives ครบ 3–4 ข้อ
- [ ] Key Concepts ครบถ้วน
- [ ] Syntax / Rules
- [ ] Runnable Code Examples
- [ ] Code Compile และ Run ได้จริง
- [ ] Common Mistakes
- [ ] Exercises 2 ข้อ พร้อม Solutions
- [ ] PPL Perspective
- [ ] Rust vs Other Language
- [ ] References อย่างน้อย 4 แหล่ง
- [ ] AI Usage Declaration
- [ ] GitHub Contribution
- [ ] สมาชิกทั้ง 4 คนมีส่วนร่วม
- [ ] สมาชิกทั้ง 4 คนพร้อมนำเสนอคนละ 5 นาที
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ของกลุ่มได้

---

## Submission Information

**Repository:** `[GitHub repository URL]`

**Chapter Path:** `[เช่น chapters/01-introduction/]`

**Final PR:** `#[PR number]`

**Submitted by:** `[Group XX]`

**Date:** `[YYYY-MM-DD]`

*โครงสร้างเอกสารฉบับเต็ม (Key Concepts, Runnable Code Examples, Common Mistakes, Exercises, PPL Perspective, Rust vs Other Language, References, AI Usage Declaration, GitHub Contribution, Final Checklist) ให้ทำต่อจากจุดนี้ตาม Template หลักของวิชา (`rust_tutorial_template.md`) ที่แนบมากับใบมอบหมายงาน*
