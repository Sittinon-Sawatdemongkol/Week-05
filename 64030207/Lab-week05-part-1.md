# การทดลองสัปดาห์ที่ 5.1 #
## ศึกษา data structure  และ methods ของ predefined type ในภาษา C#  ##


### Learning Outcome ###
1. นักศึกษารู้จัก predefined type และบอกได้ว่ามีอะไรบ้าง
2. นักศึกษารู้จักองค์ประกอบของ predefined type แต่ละชนิดและสามารถสร้างแผนภาพอธิบาย type เหล่านั้นได้

### ความรู้เบื้องต้น ###
#### 1.  Predefined type ในภาษา C# ####

Predefined type ในภาษา C# มีอยู่ด้วยกัน 16 ชนิด (สำหรับคนที่ update เป็น C# version 9 แล้ว จะมี 18 ชนิด) ดังรูปที่ 1


![](./Pictures/PredefinedType.png)


<p align = "center"> <b>รูปที่ 1</b>  predefined type ในภาษา C# </p>

#### 2. การเข้าถึง predefined type โดยใช้ Visual Studio IDE ####
เราสามารถอาศัยเครื่องมือใน text editor ของ Visual Studio เข้าถึงนิยามของ predefined type ได้โดยการกดปุ่ม F12 หรือ กดปุ่ม Ctrl บนคีย์บอร์ดแล้วใช้เมาส์คลิกที่ขื่อของ Type นั้นๆ

##### ลำดับขั้นการทดลอง #####

1. สร้าง console project ใน Visual studio สมมติว่าตั้งชื่อ project เป็น `Week05_Lab1`



2. แก้ไขไฟล์ `program.cs` มีเนื้อหาดังต่อไปนี้


```cs
class Program
{
    sbyte sb;
    byte bt;
    short sh;
    ushort ush;
    int ii;
    uint ui;
    long lo;
    ulong ul;
    float fl;
    double db;
    bool bl;
    char ch;
    decimal de;

    object ob;
    string st;
    dynamic dy;

    static void Main(string[] args)
    {

    }
}
```

<p align = "center"> <b>รูปที่ 2 </b> Source code  ของ program.cs</p>


3. กดปุ่ม Ctrl แล้วใช้เมาส์คลิกที่ `sbyte` โปรแกรม Visual Studio จะเปิดไฟล์ใหม่ขึ้นมา ซื่งมือเนื้อหาของ `System.Sbyte`

![รูปที่ 2](./Pictures/Lab5_1_Pic2.png)


จะสังเกตได้ว่าในบรรทัดที่ 12 มีการสร้าง type ของข้อมูลเป็น `struct` ซึ่งมีการ สืบทอดมาจาก `Interface` หลายชนิด (จะได้เรียนเรื่อง `interface` ในภายหลัง)

ในบรรทัดที่ 18 และ 22 มีตัวแปรแบบ `public const SByte` จำนวนสองตัว ซึ่งทำหน้าที่บอกค่าสูงสุด (`MaxValue`) และค่าต่ำสุด  (`MinValue`) ที่สามารถเก็บในตัวแปรชนิดนี้ 

จากค่า `MaxValue`  และ   `MinValue` ทำให้เรารู้ได้ว่าตัวแปรที่สร้างจาก type นี้มีขนาด 8 บิตแบบคิดเครื่องหมาย นั่นคือต้องใช้บิดซ้ายสุดจำนวน 1 บิตเป็นตัวเก็บเครื่องหมาย (ถ้าบิตนี้มีค่า 0 คือจำนวนเต็มบวก ถ้าเป็น 1 จะเป็นจำนวนเต็มลบ) ดังนั้นจึงสามารถมีข้อมูลได้ 7 บิต (แทนค่าเป็นเลขฐานสิบได้ 0-127)

`1 0000000` ถึง `1 1111111` เป็นค่าลบ

`0 0000000` ถึง `0 1111111` เป็นค่าบวก


บรรทัดที่ 27 ถึง 338 จะเป็น methods ของชนิดข้อมูลนี้ ทำให้เรารู้ว่าสามารถทำอะไรกับชนิดข้อมูลนี้ได้บ้าง  

ถ้าลองคลิ่ folding โดยการคลิกที่เครื่องหมาย [+] เราจะเห็นข้อความอธิบายอยู่ใน comment ดังรูปที่ 3

![รูปที่ 3](./Pictures/Lab5_1_Pic3.png)

<p align = "center"> <b>รูปที่ 3</b> คำอธิบาย method ของ SByte </p>

4. วาดไดอะแกรมของ type นี้ด้วย plantuml

``` puml
@startuml
class SByte
{
  + Maxvalue : SByte
  + Minvalue : SByte

  + Parse(...) : SByte 
  + TryParse(...) : SByte
  + CompareTo(...) : SByte
  + Equals(...) : bool
  + GatHashCode() : int
  + GetTypeCode() : TypeCode
  + ToString(...) : string
}
@enduml
```

เมื่อ render ด้วยโปรแกรม plantuml แล้วจะได้คลาสไดอะแกรมดังนี้

![รูปที่ 3](./Pictures/SByte_uml.png)

<p align = "center"> <b>รูปที่ 4</b> diagram สำหรับ SByte </p>


----------
__หมายเหตุ__ 

รูปแบบของการเขียนรายละเอียดของตัวแปรและ function ใน class diagram คือ
```
< +|-|# > name [ : < return-type > ]
```
เมื่อ
```
+ คือการเข้าถึงแบบ public
- คือการเข้าถึงแบบ private
# คือการเข้าถึงแบบ protected

< > หมายถึงเป็นส่วนที่ต้องมี (required)
[ ] หมายถึงเป็นส่วนที่ไม่ต้องก็ได้ (optional)

เช่น 
 + Maxvalue : SByte     //  ในกรณีที่ต้องการระบุให้ชัดเจนเนื่องจากรู้ชนิดล่วงหน้าแล้ว
 หรือ 
 + Maxvalue             // ในกรณีที่ยังไม่รู้ชนิดล่วงหน้า 

```
ในกรณีที่ชื่อฟังก์ชันเหมือนกันแต่มี parameter ต่างกันให้เขียน parameter  เป็น (...) แล้วใช้ฟังก์ชันเดียวเท่านั้น

----------

## แบบฝึกหัด ##

เขียนโค้ด plantuml สำหรับ type ชนิดอื่นๆ โดยใช้วิธีเดียวกันกับขั้นตอนที่ 3  เพื่อสร้าง diagram สำหรับ predefined type ทุกชนิด

1.sbyte

![image](https://user-images.githubusercontent.com/115066261/218466159-27448576-7f8a-4bd5-92fd-3097fbfbcc6f.png)

2.byte

![image](https://user-images.githubusercontent.com/115066261/218465501-c21ad13f-aca0-4756-9659-eb3d14ae1444.png)

3.short

![image](https://user-images.githubusercontent.com/115066261/218465694-63fc2df1-ce8d-4ed9-bf7a-5ef772821e5f.png)

4.ushort

![image](https://user-images.githubusercontent.com/115066261/218465308-248178c1-0ff9-47b8-9ee8-a0d360a08949.png)

5.int

![image](https://user-images.githubusercontent.com/115066261/218468300-dd1bb45c-497b-499b-bf3f-9a5ba4038480.png)

6.uint

![image](https://user-images.githubusercontent.com/115066261/218468732-52546f5a-1c69-4a80-98c8-c73c47a7f6ac.png)

7.long

![image](https://user-images.githubusercontent.com/115066261/218469087-ea1105dc-47b3-445b-85f6-bea08c207ebc.png)

8.ulong

![image](https://user-images.githubusercontent.com/115066261/218469439-2e5064d1-4dcb-430a-b8a1-7cefe67efedf.png)

9.float

![image](https://user-images.githubusercontent.com/115066261/218472414-02d85a27-8fca-46d3-9b67-2e8400b917e5.png)

10.double 

![image](https://user-images.githubusercontent.com/115066261/218473230-c286707d-c14d-49d4-ae2c-792ab777b563.png)

11.bool

![image](https://user-images.githubusercontent.com/115066261/218474349-0cb97fd6-17e1-4b10-b535-07341036b262.png)

12.char

![image](https://user-images.githubusercontent.com/115066261/218478318-b3b03141-a727-4395-b062-8d457d976b6d.png)

13.decimal

![image](https://user-images.githubusercontent.com/115066261/218508435-f189326b-35af-4f73-9cf6-8871119ae837.png)

14.object

![image](https://user-images.githubusercontent.com/115066261/218509029-ab5a0657-623c-47da-a577-27fbc7d70c78.png)

15.string

![image](https://user-images.githubusercontent.com/115066261/218509559-132bd1b9-400b-42fe-893d-193df074c009.png)

16.dynamic

none