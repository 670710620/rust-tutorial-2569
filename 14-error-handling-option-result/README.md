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

ในการพัตนาโปรแรมต่างๆนั้น ผู้เขียนต้องคำนึงถึงความเป็นไปได้ที่การทำงานของโปรแกรมต้องเจอกับสถานะที่ทำให้โปรแกรมทำงานผิดพลาดไปในทางที่เราไม่ต้องการ
เช่น การค้นหาไฟล์ไม่ได้ หาข้อมูลที่ต้องการไม่ได้ หรือบัคที่ทำให้ไม่สามารถดำเนินการได้
จึงมีความสำคัญที่โปรแกรมต้องสามารถชี้ถึงความผิดพลาดนั้นได้ และมีวิธีการในการรับมือเพื่อคงการทำงานต่อไป

ซึ่ง Rust เป็นภาษาที่มีแนวคิดที่ว่า ทำให้ความเป็นไปได้ในการล้มเหลวของผลลัพธ์ต่างๆเป็นชนิดข้อมูลที่บ่งบอกว่าการทำงานนั้นสำเร็จหรือไม่ 
ส่งผลให้ผู้เขียนเห็นได้ชัดเจนจาก return type ของ function ที่ใช้งาน และสามารถตัดสินใจที่รับมือกับปัญหาที่อาจเกิดขึ้นได้อย่างไร

ตัวอย่างเช่น หากฟังก์ชันมี return type เป็น Option<T><br>
```fn function(a: i32) -> Option<i32>```<br>
หมายความว่าฟังก์ชันจะมีค่าเป็นชนิด i32 หรืออาจจะไม่มีค่าให้ส่งกลับมา

Rust แยกข้อผิดพลาดเป็น 2 แบบหลัก Recoverable Errorและ Unrecoverable Error <br>
Recoverable Error เช่น "File not found" เป็นการทำงานผิดพลาดที่เราสามารถตรวจสอบ และออกแบบให้มีรับมือกับความผิดพลาดนี้เพื่อให้โปรแกรมทำงานต่อไป<br>
Unrecoverable Error เช่น การเข้าถึงตำแหน่ง array นอกเหนือจากที่สร้างไว้ ซึ่งถือว่าเป็นสิ่งที่อันตรายที่จะทำให้งานต่อไป เราจึงอาจต้องการให้มีการหยุดการทำงานของโปรแกรม โดยการเรียก panic! 

rust มีชนิดข้อมูลที่สำคัญ 2 ชนิดในการรับมือกับสถานการณ์ที่อาจต้องผบเจอกับข้อผิดพลาด คือ Option และ Result<br>
Option ใช้สำหรับรับมือกับปัญหาที่เกิดขึ้นจากข้อมูลที่ต้องการไม่มีอยู๋ และส่งกลับคืนค่าไม่ได้<br>
Result ใช้รับมือกับปัญหาที่เกิดขึ้นจากการทำงานที่ล้มเหลว และมีการส่งข้อมูลเกี่ยวกับความล้มเหลวนั้นมาได้<br>

---

## 4. Key Concepts

### 4.1 `Option`

**คำอธิบาย**

`Option<T> : enum type ที่มี 2 variant: Some(T), None
ใช้ในการรับมีการความเป็นไปได้ที่จะม่มีข้อมูลที่ต้องการในการคืนค่าออกมา 
ตัวอย่างเช่น ฟังค์ที่ใช้ค้นหาและส่งค่าคืนมาอาจข้อมูลพบ หรืออาจจะไม่พบก็ได้
ซึ่งจะไม่ได้มองว่าฟังค์ชันนั้นทำงานล้มเหลว แต่การหาไม่เจอเป็นผลลัพธ์ปกติที่ควรรับมือได้

**ตัวอย่าง**

```rust
fn main() {
    println!("Hello, Rust!");
}
```

**Explanation**

`ฟังก์ชันมี return type เป็น Option<i32> ทำให้ผลลัพธืมีได้ 2แบบคือ Some(i32) หรือ None

Some(T) ใช้แทนค่าที่สามารถหาผลลัพธ์ได้ หากการทำงานของฟังก์ชันมีค่าที่ต้องการส่งคืน ฟังก์ชันจะคืนค่า some(T) เมื่อTเป็นข้อมูลผลลัพธ์ที่ต้องการส่งคืนมา
และมี T เป็น generic type ในการใส่ผลลัพธ์ชนิดนั้น

None แทนค่าที่บ่งบอกว่าไม่สามารถหาผลลัลพธ์นั้นได้ จึงไม่มีข้อมูลอยู่ด้านในเหนือม some
ฟังก์ชันจะส่ง none กลับมาหากไม่มีข้อมูลที่ส่งคืนได้ 
`

---

### 4.2 `Result`
**คำอธิบาย**

`Result<T,E>  : enum type ที่มี 2 variant: Ok(T), Err(E)
ใช้รับมือกับความเป็นไปได้ที่มี่การล้มเหลวจากการทำงานต่างๆ เช่น ไม่สามารถอ่านไฟล์ได้เนื่องจากไฟล์นั้นไม่มีอยู่`

**ตัวอย่าง**

```rust
fn main() {
    println!("Hello, Rust!");
}
```

**Explanation**

`ฟังก์ชันมี return type เป็น Result<i32, String> ทำให้การคืนค่าได้ 2แบบคือ Ok(i32) หรือ Err(String)

Ok(T) จะถูกส่งกลับไปพร้อมกับ T (generic type) ใส่ไว้ด้านใน
ในเหตุการณืที่การทำงานนั้นสำเร็จ เช่น การเจอไฟล์ที่ต้องการ
โดย T จะแทนข้อมูลที่เราต้องการส่งกลับไปด้วย ในกรณีที่การทำงานสำเร็จ

Err(E) จะถูกส่งกลับไปพร้อมกับ E (generic type) ด้านใน
ในสถานะการที่การทำงานนั้นผิดพลาด เช่น ไม่สร้างหาไฟล์นั้นได้ หรือ ไม่สามารถสร้างไฟล์ใหม่ไม่ได้
โดย E จะแทนข้อมูลเกี่ยวความล้มเหลวจากความพยายามในการนำเนินการนั้น
`

---

### 4.3 `Match`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.4 `Error Propagation`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.5 `? operator`

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
