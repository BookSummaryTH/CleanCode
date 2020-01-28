# Meaninggful Names

```C++
public List<int[]> getFlaggedCells(){
    List<int[]> flaggedCells = new ArrayList<int[]>;
    for(int[] cell : gameBoard)
        if(cell[STATUS_VALUE] == FLAGGED)
            flaggedCells.add(cell);
    return flaggedCells;
}
```

change type int[] to type cell

```C++
public List<Cell> getFlaggedCells(){
    List<Cell> flaggedCells = new ArrayList<int[]>;
    for(Cell cell : gameBoard)
        if(cell.isFlagged())
            flaggedCells.add(cell);
    return flaggedCells;
}
```

## Avoid Disinformation

เราควรหลีกเลี่ยงคำที่มีหลายความหมาย  เช่น hp, aix, sco 

อย่าอ้างอิงถึง grouping of accout เป็น accoutList เว้นแต่เป็น List จริงๆ
บางคำนั้นมีความหมายเฉพาะกับ programer ทำให้สรุปผิดพลาด ใช้ accouts อย่างเดียวจะดีกว่า

## Make Meaningful Distinctions สร้างความแตกต่างที่มีความหมาย

programer สร้างปัญหาด้วยตัวเอง เช่น same name refer to different things in the same scope

คำฟุ่มเฟือยมีความหมายที่สร้างความแตกต่าง  

ลองจิตนาการ `Product` class ถ้าคุณมีการเรียกอื่น ๆ  `ProductInfo` or `ProductData`

คุณทำให้ชื่อแตกต่างโดย `Info` และ `Data`แต่มันไม่ชัดเจน  เหมือนกับ `a`, `an` , `the`

### Prefix

โปรดทราบว่าคำนำหน้า `a` and `the` มันสร้างความหมายที่แตกต่าง

เช่น `a`  for all local variables and `the` for all function arguments

ปัญหาจะมาเช่น ตัวแปร theZork แต่คุณดันมี zork อยู่แล้ว

### คำซ้ำซ้อน

เช่นการใช้คำว่า table  ไม่ควรปรากฎบนชื่อ table  หรือ NameString ทีมี type String อยู่แล้ว

ลองจิตนาการ class `Customer` และอื่นๆ `CustomerObject` คุณจะเข้าใจความแตกต่างได้ยังไง ?

อันไหนแสดงถึง best path to customer's playment history ?

้นี้คือตัวอย่างของความผิดพลาด

```C++
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

programmer จะรู้ได้ยังไงว่าต้องเรียกอันไหน ในกรณีที่ไม่ได้สนใจ specific conventions 

ตัวแปร `moneyAmout` จะแยกไม่ออกจาก `money`

`customerInfo`  จะแยกไม่ออกจาก `customer`

`accoutData` แยกไม่ออกจาก `accout`

`theMessage` แยกไม่ออกจาก `message`

## Use Pronounceable Names

Human are good at word, ส่วนสำคัญของสมองอุทิศให้กับแนวคิดของคำ

A company I know has genymdhms (generation date, year, month, day, hour, minute,
and second)

ดังนั้นพวกเขาจึงเดินไปพูดว่า  “gen why emm dee aich emm ess”. I have an

annoying habit of pronouncing everything as written, so I started saying “gen-yah-muddahims.”

so I started saying “gen-yah-muddahims.” It later was being called this by a host of designers and 

analysts, and we still sounded silly

```C++
class DtaRcrd102{
    private Date genymdhms;
    private Date modymdhms;
    private final Sting pszqint =  "102";
}

class Customer {
    private Date generationTimestamp;
    private Date modificationTimestamp;;
    private final String recordId = "102";
/* ... */
};
```

## Use Searchable Names ใช้ชื่อที่ค้นหาได้

เวลา ctrl+F ถ้าเราใช้ชื่อทีมีโอกาสปรากกฎสูงก็จะเป็นปันหาในการค้นหาเช่นชื่อ trumps

ความเห็นส่วนตัวของฉันคือ singgle-letter name  สามารถใช้ใน short methods ได้
_ความยาวของชื่อขึ้นอยู่กับขนาดของscope_

```C++
for (int j=0; j<34; j++) {
    s += (t[j]*4)/5;
}
```

```C++
int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;
int sum = 0;
for (int j=0; j < NUMBER_OF_TASKS; j++) {
    int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
    sum += realTaskWeeks;
}
```

## Hungarian Notation

[read more hungarian...](http://web.mst.edu/~cpp/common/hungarian.html)

```C++
PhoneNumber phoneString;
// name not changed when type changed!
```

## Member Prefixes

คุณไปจำไม่เป็นต้องนำหน้าตัวแปรด้วย `m_`

```C++
public class Part {
private String m_dsc; // The textual description
    void setName(String name) {
        m_dsc = name;
    }
}
```

```C++
public class Part {
    String description;
    void setDescription(String description) {
        this.description = description;
    }
}
```

## Interface and Implementations

กรณีพิเศษสำหรับการ encodings ตัวอย่างเช่น คุณ build ABSTRACT FACTORY for create shapes 

และคุณจะนำมันไปใช้ คุณควรจะตั้งชื่อมันว่าอะไร ? `IShapeFactory` `ShapeFactory`

การมี `I` ทำให้รู้ว่าคุณใช้ interface  ฉันต้องการให้เขารู้ว่ามันคือ  `ShapeFactory` เท่านั้น 

ดังนั้นควรตั้งชื่อว่า `ShapeFactoryImp` or `CShapeFactory`

## Avoid Mental Mapping

ผู้อ่านไม่จำเป็นต้องแปลชื่อของคุณเป็นชื่ออื่นที่พวกเขารู้อยู่แล้ว

This is a problem with single-letter variable names , แน่นอน  loop counter อาจจะเป็น `i`,`j`,`k` ((though never `l`!))

หากขอบเขตมีขนาดเล็กมากและไม่มีชื่ออื่นที่ขัดแย้งกับมัน

นี่เป็นเพราะชื่อตัวอักษรเดียวสำหรับเคาน์เตอร์วนซ้ำเป็นแบบดั้งเดิม

อย่างไรก็ตามในบริบทอื่น ๆ ส่วนใหญ่ชื่อตัวอักษรเดียวเป็นตัวเลือกที่ไม่ดี

ไม่มีเหตุผลที่แย่กว่านี้สำหรับการใช้ชื่อ c มากกว่าเพราะ a และ b ถูกใช้ไปแล้ว

## Class Names

classes or objects ควรจะเป็น คำนามหรือวลีเช่น  `Customer`, `WikiPage`, `Accout`, `AddressParser`

Avoid words like `Manager`, `Procressor`, `Data`, `Info` 

## Method Names

method ควรจะเป็น verb หรือวลี เหมือนกับ `postPayment`, `deletePage`, `save`

Accessors, mutators และ predicates ควรตั้งชื่อ `get`, `set` , `is` according to java standard

```Java
string name = employee.getName();
customer.setName("mike");
if (paycheck.isPosted())...

```

When constructors are overloaded, use static factory methods with names that
describe the arguments. For example,

```Java
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

โดยทั่วไปดีกว่า

```Java
Complex fulcrumPoint = new Complex(23.0);
```

## Don't Be Cute

