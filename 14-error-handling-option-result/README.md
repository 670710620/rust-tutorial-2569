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
| 4 | นายณัฐวีร์ บุญยินดี | 670710622 | `@[670710622]` | Exercises + Common Mistakes + Challenge (แบบฝึกหัด + ข้อผิดพลาดที่พบบ่อย + คำถามท้าทาย) |

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
fn read_port(input: &str) -> u16 {
    input.trim().parse().unwrap() // panics if input is not a valid number
}

fn main() {
    let config = "8080"; // try changing this to "abc"

    let port = read_port(config);
    println!("Starting server on port {}", port);
}
```

**Correct Code**

```rust
use std::num::ParseIntError;

fn read_port(input: &str) -> Result<u16, ParseIntError> {
    let port: u16 = input.trim().parse()?; // returns Err to the caller instead of panicking
    Ok(port)
}

fn main() {
    let config = "abc"; // try changing this to "abc"

    match read_port(config) {
        Ok(port) => println!("Starting server on port {}", port),
        Err(e) => println!("Invalid config: {}", e),
    }
}
```

**Why?**

`เพราะ .unwrap() ตรวจเจอข้อผิดพลาดแล้ว panic จะทำการ crash โปรแกรม แต่ถ้าเราใช้ ? แทนนั้น Errจะถูกส่งกลับไปให้ caller เลือกวิธีจัดการ`

---

### Mistake 2 — `[Matching on error strings instead of error variants.]`

**Problem**

`Developer บางคนมักเช็กข้อผิดพลาดด้วยการดูข้อความ เช่น err.contains("not found") ซึ่งเปราะบางมาก เพราะข้อความ error เปลี่ยนได้ทุกเมื่อ เช่น แก้คำ แก้ภาษา หรือเปลี่ยนรูปแบบ พอข้อความเปลี่ยน โค้ดยังคอมไพล์ผ่านตามปกติ แต่เงื่อนไขที่เช็กไว้จะไม่ทำงานอีกต่อไปโดยไม่มีอะไรเตือนเลย`

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
enum AppError {
    UserNotFound,
    DatabaseDown,
}

fn find_user(id: u32) -> Result<String, AppError> {
    match id {
        1 => Ok("Alice".to_string()),
        99 => Err(AppError::DatabaseDown),
        _ => Err(AppError::UserNotFound),
    }
}

fn main() {
    let id = 2; // try 1 (found), 2 (not found), 99 (database down)

    match find_user(id) {
        Ok(name) => println!("Hello {}", name),
        Err(AppError::UserNotFound) => println!("Creating a new user..."),
        Err(AppError::DatabaseDown) => println!("Try again later"),
    }
}
```

**Why?**

`การเช็ก error ด้วย String ทำให้โค้ดต้องไปพึ่งพาข้อความที่เขียนไว้ ซึ่งคอมไพเลอร์ไม่ได้ช่วยตรวจสอบตรงนี้ ถ้ามีการเปลี่ยนข้อความจาก user not found เป็น no such user โค้ดที่ใช้ตรวจจับ error ก็อาจไม่ทำงานโดยที่เราไม่รู้ตัว แต่ถ้าใช้ enum เราสามารถกำหนดประเภทของ error ไว้ชัดเจน ทำให้ Rust สามารถตรวจสอบผ่านระบบ type ได้
`

---

## 8. Exercises

> จัดทำแบบฝึกหัด **2 ข้อ** ที่สอดคล้องกับ Topic และมีระดับความยากเหมาะสม

### Exercise 1 — หาเลขคู่ตัวแรก (Option)

**Problem**

เขียนฟังก์ชัน `first_even` ที่รับ slice ของ `i32` แล้วคืนค่าเลขคู่ตัวแรกที่พบ
โดยมี return type เป็น `Option<i32>` (ถ้าไม่มีเลขคู่ให้คืน `None`)
จากนั้นใน `main` ให้ใช้ `match` แสดงผลทั้งสองกรณี

**Hint**

ใช้ loop ตรวจทีละตัว ถ้า `n % 2 == 0` ให้ `return Some(n)` และถ้าจบ loop แล้วยังไม่เจอให้คืน `None`

**Solution**

```rust
fn first_even(numbers: &[i32]) -> Option<i32> {
    for &n in numbers {
        if n % 2 == 0 {
            return Some(n);
        }
    }
    None
}

fn main() {
    match first_even(&[1, 3, 4, 7]) {
        Some(n) => println!("First even number: {}", n),
        None => println!("No even number found."),
    }

    match first_even(&[1, 3, 5]) {
        Some(n) => println!("First even number: {}", n),
        None => println!("No even number found."),
    }
}
```

**Expected Output**

```text
First even number: 4
No even number found.
```

**Explanation**

ฟังก์ชันวนตรวจตัวเลขทีละตัว ถ้าเจอเลขคู่จะคืน `Some(n)` ทันที แต่ถ้าวนจนครบแล้วไม่เจอ จะคืน `None`
ใน `main` เราใช้ `match` จัดการทั้ง 2 กรณี (`Some` / `None`) ซึ่ง Rust บังคับให้เราจัดการครบทุกกรณี จึงไม่มีโอกาสลืมเช็กกรณีที่ไม่มีค่า

---

### Exercise 2 — บวกเลขจากข้อความ (Result และ ?)

**Problem**

เขียนฟังก์ชัน `add_strings` ที่รับข้อความ 2 ตัว (`&str`) แปลงเป็น `i32` แล้วคืนผลบวก
โดยมี return type เป็น `Result<i32, ParseIntError>` และต้องใช้ `?` ในการส่ง error กลับ (ห้ามใช้ `unwrap`)

**Hint**

ใช้ `.parse::<i32>()?` กับข้อความแต่ละตัว ถ้าแปลงไม่ได้ `?` จะ return `Err` ออกจากฟังก์ชันให้อัตโนมัติ
อย่าลืม `use std::num::ParseIntError;`

**Solution**

```rust
use std::num::ParseIntError;

fn add_strings(a: &str, b: &str) -> Result<i32, ParseIntError> {
    let x = a.trim().parse::<i32>()?;
    let y = b.trim().parse::<i32>()?;
    Ok(x + y)
}

fn main() {
    println!("{:?}", add_strings("10", "20"));
    println!("{:?}", add_strings("10", "abc"));
}
```

**Expected Output**

```text
Ok(30)
Err(ParseIntError { kind: InvalidDigit })
```

**Explanation**

`parse::<i32>()` คืนค่าเป็น `Result` ถ้าแปลงสำเร็จ `?` จะดึงค่าออกมาใช้ต่อ แต่ถ้าล้มเหลว (เช่น `"abc"`)
`?` จะ return `Err` กลับไปให้ผู้เรียกทันที โดยบรรทัด `Ok(x + y)` จะไม่ถูกรัน
วิธีนี้ปลอดภัยกว่า `unwrap` ที่จะทำให้โปรแกรม panic (ตรงกับ Common Mistake ข้อ 1)

---

## 9. PPL Perspective

> **ส่วนนี้เป็นหัวใจของรายวิชา Principles of Programming Languages**

วิเคราะห์ Topic นี้ในมุมมองของ Programming Languages

### 9.1 Syntax

`[Topic นี้เกี่ยวข้องกับ syntax อย่างไร]`

### 9.2 Semantics

`[คำสั่ง/construct เหล่านี้มีความหมายหรือพฤติกรรมอย่างไร]`

### 9.3 Type System

`[เกี่ยวข้องกับ type system อย่างไร ถ้ามี]`

### 9.4 Memory / Resource Management

`[เกี่ยวข้องกับ memory หรือ resource management อย่างไร ถ้ามี]`

### 9.5 Abstraction / Other PPL Concepts

`[อธิบาย abstraction, scope, binding, paradigm หรือแนวคิด PPL อื่นที่เกี่ยวข้อง]`

### 9.6 Why Rust?

`[Rust ใช้แนวคิดนี้เพื่อเพิ่ม safety, reliability หรือ performance อย่างไร]`

---

## 10. Rust vs. Other Language

**Comparison Language:** `[Python / C / C++ / Java / Kotlin / ...]`

| Aspect | Rust | Other Language |
|---|---|---|
| Syntax | `[อธิบาย]` | `[อธิบาย]` |
| Semantics / Behavior | `[อธิบาย]` | `[อธิบาย]` |
| Type System | `[อธิบาย]` | `[อธิบาย]` |
| Memory Management | `[อธิบาย]` | `[อธิบาย]` |
| Safety | `[อธิบาย]` | `[อธิบาย]` |

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
