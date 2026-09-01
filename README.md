# មេរៀន OOP ជាមួយ C# (Object-Oriented Programming)

## សេចក្ដីផ្ដើម
OOP (Object-Oriented Programming) ជាទម្រង់នៃការសរសេរកូដ (Programming Paradigm) ដែលផ្ដោតលើការប្រើប្រាស់ **Objects**។ 
ឯកសារនេះជាការចងក្រងសង្ខេបរបស់ខ្ញុំសម្រាប់មុខវិជ្ជា OOAD ថ្នាក់បរិញ្ញាបត្រឆ្នាំទី៤ នៃសាកលវិទ្យាល័យភូមិន្ទភ្នំពេញ (RUPP) ប៉ុណ្ណោះ បើមានកំហុសសូមអធ្យាស្រ័យ។

---

## 1. Class និង Objects

* **Class**: ជាពុម្ពគំរូ (Blueprint) សម្រាប់បង្កើត Object។ វាជា Source Code ដែលគេអាចកំណត់នូវ data, properties, methods, events លក្ខខណ្ឌផ្សេងៗតម្រូវទៅតាម object ដែលយើងចង់បាន។
* **Object**: ជារបស់ ឬវត្ថុដែលកើតចេញពី Class (Instance of a class)។

នៅក្នុង C# (ជាពិសេសការសរសេរកម្មវិធីមាន UI ដូចជា WinForms) មាន ៣ របៀបចម្បងដែលអាចបង្កើត Object ចេញពី Class បាន៖
1. តាមរយៈការគូសទាញ (Drag & Drop ពី Toolbox មកលើ Form)
2. តាមរយៈការសរសេរកូដ (Instantiating using `new` keyword)
3. System ជាអ្នក Generate ឱ្យដោយស្វ័យប្រវត្តិ

**Syntax:**
```csharp
class ClassName
{
    // Members (Fields, Properties, Methods)
}

```

---

## 2. Class Members

Class​ Members មួយជាទូទៅរួមមាន៖

### i) Data (Field)

ជាទីតាំង (Variable) សម្រាប់ផ្ទុកតម្លៃក្នុង Memory។ Field អាចប្រើជាទម្រង់ Scalar (តម្លៃតែមួយ) ឬ Array (សំណុំតម្លៃ)។

```csharp
class ClsTest1
{
    public int x;
    public string y;
}

// របៀប call មកប្រើ
ClsTest1 obj1 = new ClsTest1();
obj1.x = 10;
int t1 = obj1.x;

obj1.y = "ABC";
string t2 = obj1.y;

```

### ii) Property (លក្ខណៈសម្គាល់)

Property ដូចជា ឈ្មោះ, ភេទ, អាយុ ជាដើម។ នៅក្នុង C# Property ជា Block of code ដែលប្រើដើម្បី Access (Read/Write) ទៅកាន់ private data (Field) ដោយសុវត្ថិភាព។
គោលការណ៍ OOP ច្រើនណែនាំឱ្យ Access data តាមរយៈ Property។

**Syntax:**

```csharp
public DataType PropertyName
{
    get { return variable; } // Read
    set { variable = value; } // Write
}

```

**ឧទាហរណ៍ទី១ (Full Property):**

```csharp
class ClsTest1
{
    private int _x;
    private string _y;

    public int PX
    {
        get { return _x; }
        set { _x = value; }
    }
    public string PY
    {
        get { return _y; }
        set { _y = value; }
    }
}

```

**ឧទាហរណ៍ទី២ (Auto-Implemented Property):**
ប្រើនៅពេលដែលយើងមិនចាំបាច់ដាក់លក្ខខណ្ឌ (Logic) បន្ថែមពេល Read ឬ Write។

```csharp
class ClsTest2
{
    public int PX { get; set; }
    public string PY { get; set; }
}

```

> **សំណួរពិចារណា៖** តើរវាង public field និង Property គួរប្រើមួយណានៅពេលណា? ហេតុអ្វី? (ចម្លើយខ្លី៖ Property ផ្ដល់សុវត្ថិភាពទិន្នន័យ ការពារការបញ្ចូលតម្លៃខុស និងអាចធ្វើ Data Binding បាន ដូច្នេះគួរប្រើ Property ជានិច្ចសម្រាប់ public access)។

### iii) Method (សមត្ថភាព ឬសកម្មភាព)

Method ជា Block of code សម្រាប់ធ្វើការងារជាក់លាក់ណាមួយ។

* **Method មិន Return Value (ប្រើ `void`):**

```csharp
public void MethodName(ParameterList)
{
    // Implementation
}

```

* **Method ដែល Return Value:**

```csharp
public ReturnType MethodName(ParameterList)
{
    // Implementation
    return value;
}

```

**ចំណាំលើ Parameters ក្នុង Method:**

* **Parameter**: ជា Local variable ប្រកាសក្នុងវង់ក្រចករបស់ Method សម្រាប់ត្រៀមទទួលតម្លៃ។
* **Argument**: ជាតម្លៃផ្ទាល់ដែលត្រូវបានបញ្ជូនទៅពេល Call Method នោះ។
* **Pass by Value (Default)**: ពេល parameter ដូរតម្លៃក្នុង Method វាមិនធ្វើឱ្យ argument នៅខាងក្រៅដូរតម្លៃតាមទេ។
* **Pass by Reference (ប្រើ `ref` ឬ `out`)**: បើ parameter ដូរតម្លៃ នោះ argument ដើមនៅខាងក្រៅក៏ដូរតម្លៃតាមដែរ។

---

## 3. Method Overloading

Method Overloading ជាការបង្កើត Method ច្រើនដែលមាន **ឈ្មោះដូចគ្នា** នៅក្នុង Class តែមួយ ប៉ុន្តែត្រូវខុសគ្នាត្រង់៖

* ចំនួន Parameters ខុសគ្នា
* ឬ Datatype របស់ Parameters ខុសគ្នា

```csharp
class ClsTest
{
    public void M1() { }
    public int M1(int t) { return t; }
    public string M1(string s) { return s; }
    public void M1(int t1, int t2) { }
    // These are called "Overloaded Versions"
}

```

**អត្ថប្រយោជន៍៖**

* ប្រើប្រាស់ឈ្មោះ Method តែមួយអាចធ្វើការងារបានច្រើនទម្រង់ (ងាយស្រួលចងចាំ)។
* កូដមានភាពស្អាត និងងាយស្រួលហៅប្រើ (ពេលវាយសញ្ញា `.` វានឹងលោត List Versions ឱ្យរើស)។

---

## 4. Constructor

Constructor ជា Method ពិសេសដែល៖

1. មានឈ្មោះ **ដូចគ្នាបេះបិទ** ទៅនឹងឈ្មោះ Class
2. **គ្មាន Return Type** (សូម្បីតែ `void` ក៏គ្មានដែរ)
3. ត្រូវបាន Call ដោយស្វ័យប្រវត្តិនៅពេលមានការបង្កើត Object (`new`)។ វាត្រូវ Call តែម្ដងគត់សម្រាប់ Object មួយ។

**ប្រភេទនៃ Constructor មាន៖**

1. **Default Constructor**: គ្មាន Parameter ប្រើសម្រាប់ Assign តម្លៃលំនាំដើម។
2. **Parameterized Constructor**: មាន Parameter ប្រើពេលចង់ទាញតម្លៃពីខាងក្រៅមកផ្ដល់ឱ្យ Object ពេលវាចាប់ផ្ដើម។
3. **Copy Constructor**: សម្រាប់ Copy ទិន្នន័យពី Object មួយដែលមានស្រាប់ ទៅឱ្យ Object ថ្មី។
4. **Static Constructor**:

* មានតែមួយគត់ក្នុងមួយ Class និងគ្មាន Access Modifier (`public`, `private` ជាដើម) ព្រមទាំងគ្មាន Parameter។
* ប្រើដើម្បីផ្ដល់តម្លៃឱ្យ Static Data។
* ត្រូវបានហៅប្រើដោយស្វ័យប្រវត្តិ មុនពេល Object ដំបូងត្រូវបង្កើត ឬមុនពេល Static Member ណាមួយត្រូវហៅប្រើលើកដំបូង។

```csharp
class ClsTest
{
    static int x;
    
    // Static Constructor គ្មាន Access Modifier ទេ
    static ClsTest() 
    { 
        x = 100; 
    }
    
    public static int M1() { return x * 100; }
}

```

5. **Private Constructor**: ប្រើសម្រាប់រារាំងមិនឱ្យគេបង្កើត Object ពីក្រៅ Class ផ្ដេសផ្ដាស (ឧទាហរណ៍៖ ការប្រើប្រាស់ក្នុង Singleton Pattern)។

```csharp
class ClsSingle
{
    private static ClsSingle _instance = new ClsSingle();
    
    private ClsSingle() { } // មិនអាច new ពីក្រៅបានទេ
    
    public static ClsSingle CreateInstance()
    {
        return _instance;
    }
}
// របៀបប្រើ
ClsSingle Obj1 = ClsSingle.CreateInstance();
ClsSingle Obj2 = ClsSingle.CreateInstance();
// Obj1 និង Obj2 គឺជា Object តែមួយនៅលើ Memory

```

---

## 5. Member Types (ប្រភេទរបស់ Class Member)

1. **Instance Member**: ជា Member ដែលជាប់ជាមួយ Object នីមួយៗផ្ទាល់ (ត្រូវប្រើតាមរយៈ Object: `obj.Method()`)។ Object ខុសគ្នា មានទិន្នន័យខុសគ្នា។

```csharp
class ClsStudent
{
    // Instance Members
    public string ID { get; set; }
    public string Name { get; set; }
}

ClsStudent stu1 = new ClsStudent();
stu1.Name = "Dara"; // ទិន្នន័យជាប់ជាមួយ stu1

```

2. **Static Member**: ជា Member របស់ Class ទាំងមូល។ វាត្រូវបានប្រើប្រាស់រួមគ្នារវាងគ្រប់ Objects ទាំងអស់ (ហៅប្រើតាមរយៈឈ្មោះ Class: `ClassName.Method()`)។

```csharp
class MathHelper
{
    // Static Member
    public static double PI = 3.14159;
}

// ហៅប្រើដោយមិនបាច់ new object
double p = MathHelper.PI;

```

---

## 6. Static Class

* មិនអាចប្រើប្រាស់ `new` ដើម្បីបង្កើត Object ពីវាបានទេ និងមិនអាចធ្វើជា Base Class (Inherit) ឱ្យគេបានទេ។
* Member ទាំងអស់របស់វាសុទ្ធតែត្រូវតែជា Static។
* ហេតុផលដែលប្រើ៖ ច្រើនប្រើសម្រាប់ប្រមូលផ្ដុំ Utility/Helper methods ដែលទាមទារការហៅប្រើញឹកញាប់ដោយមិនបាច់បង្កើត Object នាំឱ្យខាត Memory។

```csharp
// ឧទាហរណ៍ Static Class
static class Calculator
{
    public static int Add(int a, int b) { return a + b; }
    // កូដផ្សេងទៀតសុទ្ធតែត្រូវតែ static ទាំងអស់
}
// របៀបប្រើ: int sum = Calculator.Add(5, 10);

```

---

## 7. The Features of OOP (គោលការណ៍គ្រឹះនៃ OOP)

### a) Encapsulation (ការវេចខ្ចប់)

ជាវិធីសាស្ត្រក្នុងការវេចខ្ចប់ Data (Variables) និង Code (Methods) បញ្ចូលគ្នាទៅក្នុង Object តែមួយ ហើយលាក់កំបាំងភាពស្មុគស្មាញ (ឬការពារទិន្នន័យ) ពីពិភពខាងក្រៅដោយប្រើ Access Modifiers ដូចជា `private` រួចអនុញ្ញាតឱ្យ Access វិញតាមរយៈ `public` Properties ឬ Methods។

```csharp
class BankAccount
{
    // លាក់ទិន្នន័យមិនឱ្យគេ access ផ្ទាល់ (Encapsulated)
    private double _balance;

    // ផ្ដល់សិទ្ធិ access តាមរយៈ Property ព្រមទាំងមានលក្ខខណ្ឌ
    public double Balance
    {
        get { return _balance; }
        set 
        { 
            if (value >= 0) 
                _balance = value; 
        }
    }
}

```

---

### b) Inheritance (ការស្នងលក្ខណៈសម្បត្តិ)

ជាដំណើរការដែល Class ថ្មី (Derived Class / Child Class) អាចទទួលយក Members (Data, Properties, Methods) ពី Class ដែលមានស្រាប់ (Base Class / Parent Class)។ `Base <- Derived`

```csharp
class ClsBase
{
    public int Px { get; set; }
    public void M1() { }
}

class ClsDerived : ClsBase
{
    public int Py { get; set; }
    public void M2() { }
}

```

**i. Accessibility ក្នុងការស្នង:**

| Modifier | Class itself | Derived Class | Outside Class |
| --- | --- | --- | --- |
| **Private** | Yes | No | No |
| **Protected** | Yes | Yes | No |
| **Public** | Yes | Yes | Yes |

**ii. Constructor ក្នុង Inheritance:**
ក្នុង C#, Derived Class មិនបាន inherit Constructor ពី Base Class ទេ ប៉ុន្តែរាល់ពេលបង្កើត Object ពី Derived Class វាចាំបាច់ត្រូវហៅ Constructor របស់ Base Class មុនជានិច្ច (ប្រើ keyword `base`)។

```csharp
class ClsBase
{
    public ClsBase(int x) { }
}
class ClsDerived : ClsBase
{
    // ត្រូវហៅ base constructor
    public ClsDerived(int x) : base(x) { }
}

```

**iii. Virtual Method (ការកែប្រែ Method ចាស់):**
Base Class ត្រូវផ្ដល់សិទ្ធិឱ្យគេកែប្រែដោយដាក់ keyword `virtual`។ ចំណែក Derived Class ពេលចង់កែប្រែ(Implement ថ្មី) ត្រូវប្រើ keyword `override`។ បើចង់ហៅកូដចាស់មកប្រើបន្ថែម គេប្រើ `base.MethodName()`។

```csharp
class ClsBase
{
    public virtual void Display() { /* Default code */ }
}

class ClsEmployee : ClsBase
{
    public override void Display() 
    { 
        // New Implementation code
        base.Display(); // ហៅកូដពី Base មកដំណើរការដែរ
    }
}

```

**iv. Hiding Method (ការលាក់ Method ចាស់):**
បើ Base Class មិនបានដាក់ `virtual` ទេ តែ Derived Class ចង់កែសម្រួល ឬសរសេរ Method ឈ្មោះហ្នឹងដដែល នោះវាត្រូវប្រើ keyword `new` ដើម្បីប្រាប់កុំព្យូទ័រថាវាជារបស់ថ្មីដាច់ដោយឡែក ដែលលាក់បាំង Method របស់ Base Class ពេលហៅតាម Derived Class។

```csharp
class ClsBase
{
    public void M1(int t) { /* កូដដើម */ }
}

class ClsEmployee : ClsBase
{
    // ប្រើ new ដើម្បីលាក់ M1 របស់ ClsBase ពេលហៅតាម ClsEmployee
    public new string M1(int t) 
    { 
        return "Implementation ថ្មី"; 
    }
}

```

**v. Abstract Class & Abstract Method:**

* **Abstract Class**: បង្កើតដោយ keyword `abstract`។ មិនអាចយកទៅបង្កើត Object ផ្ទាល់បានទេ ប្រើសម្រាប់ធ្វើជា Base Class only។
* **Abstract Method**: ជា Method ដែលមានតែឈ្មោះ (គ្មាន Body គ្មានកន្លែងសរសេរកូដ `{...}`) ក្នុង Abstract Class។ វាបង្ខំឱ្យ Derived Class ទាំងអស់ **ដាច់ខាតត្រូវតែ** Implement វាតាមរយៈ `override`។

```csharp
abstract class Shape
{
    // Abstract Method (គ្មាន Body)
    public abstract double GetArea();
}

class Circle : Shape
{
    public double Radius { get; set; }
    
    // ដាច់ខាតត្រូវតែ Override ពី Abstract class ខាងលើ
    public override double GetArea()
    {
        return 3.14159 * Radius * Radius;
    }
}

```

**vi. Interface:**
Interface ជាក្បួនរចនាសម្ព័ន្ធ (Contract) ដែលមានកម្រិតតឹងរ៉ឹងជាង Abstract Class៖

* Interface ជា System Type (ដូច Class)
* បង្កើតដោយ keyword `interface` ហើយឈ្មោះភាគច្រើនផ្ដើមដោយអក្សរ `I`
* ជាទូទៅគ្មាន Data member (Fields) ទេ
* Members ទាំងអស់ត្រូវបានចាត់ទុកជា `public abstract` ដោយស្វ័យប្រវត្តិ គ្មាន Body (លើកលែងតែ C# version ថ្មីៗដែលអាចមាន Default Implementation)
* Inteface អាច inherit ពី Interface បាន
* Class មួយអាច **Inherit ពី Class បានតែមួយ** ប៉ុន្តែអាច **Implement ពី Interface បានច្រើន**។ មិនអាចបង្កើត Object ពី Interface ផ្ទាល់បានឡើយ។

```csharp
interface IAnimal
{
    void Speak(); // គ្មានកន្លែងសរសេរកូដទេ
}

class Dog : IAnimal
{
    // អនុវត្តកូដពេល Implement Interface
    public void Speak()
    {
        Console.WriteLine("Woof!");
    }
}

```

**vii. Sealed Class & Sealed Method:**

* **Sealed Class**: ប្រើ keyword `sealed` ដើម្បីរារាំងមិនឱ្យ Class ផ្សេងអាច Inherit ពីវាបាន (បញ្ចប់វង្សត្រកូលត្រឹមហ្នឹង)។ វាអាចបង្កើត Object ប្រើបានធម្មតា។
* **Sealed Method**: ប្រើនៅពេល Class មួយកែប្រែ (`override`) Method ពី Base class របស់វា ហើយវាមិនចង់ឱ្យកូនរបស់វា (Derived-classes) កែប្រែ Method នេះបានបន្តទៀត វាត្រូវប្រើ `sealed override`។

```csharp
class ClsBase
{
    public virtual void M1() { }
}

class ClsDerived1 : ClsBase
{
    public override void M1() { }
}

class ClsDerived2 : ClsDerived1
{
    // បញ្ឈប់ការ Override ត្រឹមនេះ (Class កូនៗរបស់វាមិនអាច override M1 បានទៀតទេ)
    public sealed override void M1() { }
}

// Sealed Class
sealed class FinalClass
{
    // មិនអាចមាន Class ណា Inherit ពី FinalClass ទេ
}

```

---

### c) Polymorphism (ពហុទម្រង់)

Polymorphism មានន័យថា "មានទម្រង់ច្រើន" (One name, many forms)។ វត្ថុតែមួយអាចបង្ហាញសកម្មភាពខុសគ្នាអាស្រ័យលើស្ថានភាព ឬកាលៈទេសៈ។

នៅក្នុង C# OOP, Polymorphism ចែកជាពីរធំៗ៖

1. **Compile-time Polymorphism (Static Binding):** សម្រេចបានតាមរយៈ **Method Overloading**។ កុំព្យូទ័រដឹងថាតើត្រូវហៅ Method មួយណាដំណើរការនៅពេល Compile អាស្រ័យលើចំនួន ឬប្រភេទ Parameter ដែលបញ្ជូនទៅ។

```csharp
// ឧទាហរណ៍ Method Overloading
class Calculator
{
    public int Add(int a, int b) { return a + b; }
    public double Add(double a, double b) { return a + b; }
}

```

2. **Run-time Polymorphism (Dynamic Binding):** សម្រេចបានតាមរយៈ **Method Overriding** (ប្រើ `virtual` / `override`)។ កុំព្យូទ័រមិនអាចកំណត់ Method ច្បាស់លាស់ឡើយលុះត្រាតែកម្មវិធីដើរ (Run-time) ដោយវាផ្អែកលើប្រភេទពិតប្រាកដរបស់ Object។

```csharp
// ឧទាហរណ៍ Method Overriding ពេល Runtime
ClsBase obj = new ClsEmployee(); // ប្រកាសជា Base តែបង្កើតជា Derived
obj.Display(); // វានឹងដំណើរការ Method Display នៅក្នុង ClsEmployee ពេលកូដកំពុង Run

```

---

## មូលហេតុដែល OOP បង្កើត Polymorphism ទាំង ២ ប្រភេទនេះមក គឺដើម្បីដោះស្រាយបញ្ហាខុសគ្នា និងផ្ដល់ភាពងាយស្រួលដល់អ្នកសរសេរកូដក្នុងកាលៈទេសៈផ្សេងៗគ្នា។

ខាងក្រោមនេះជាហេតុផលពិតប្រាកដដែលយើងត្រូវការវាទាំងពីរ៖

### ១. ហេតុអ្វីទើបត្រូវមាន Compile-time Polymorphism (Method Overloading)?

គោលបំណងចម្បងរបស់វាគឺ **"ភាពងាយស្រួលអាន (Readability) និងភាពងាយស្រួលប្រើប្រាស់ API"**។

* **បើគ្មានវាទេ៖** អ្នកនឹងត្រូវបង្កើត Method ដែលមានឈ្មោះខុសៗគ្នារាប់សិប សម្រាប់ធ្វើការងារតែមួយ។ ឧទាហរណ៍ បើចង់បូកលេខ អ្នកត្រូវសរសេរ `AddInt(int a, int b)`, `AddDouble(double a, double b)`, `AddThreeInts(int a, int b, int c)` ជាដើម។ វាធ្វើឱ្យពិបាកចាំឈ្មោះ Method ណាស់។
* **ពេលមានវា៖** អ្នកគ្រាន់តែចាំឈ្មោះ Method តែមួយគឺ `Add()`។ ពេលអ្នកហៅប្រើ ហើយបោះតម្លៃចូល (ឧទាហរណ៍ បោះលេខទសភាគ) កុំព្យូទ័រ (Compiler) ឆ្លាតល្មមនឹងរើសយក `Add(double, double)` មកដំណើរការឱ្យដោយស្វ័យប្រវត្តិ។
* **ល្បឿន (Performance):** វាមិនមានភាពយឺតយ៉ាវពេលកម្មវិធីកំពុងដើរ (Run) នោះទេ ព្រោះកុំព្យូទ័របានរៀបចំសម្រេចចិត្តរួចរាល់តាំងពីពេល Compile ម្ល៉េះ។

---

### ២. ហេតុអ្វីទើបត្រូវមាន Run-time Polymorphism (Method Overriding)?

គោលបំណងចម្បងរបស់វាគឺ **"ភាពបត់បែន (Flexibility) និងការកាត់បន្ថយការសរសេរលក្ខខណ្ឌ (if-else) ញឹកញាប់"**។ វត្ថុ (Object) ខុសគ្នា គួរតែមានសិទ្ធិឆ្លើយតបនឹងបញ្ជាតែមួយ ក្នុងទម្រង់ខុសៗគ្នា។

* **ស្រមៃមើលស្ថានភាពជាក់ស្ដែង៖** អ្នកមានប្រព័ន្ធគ្រប់គ្រងបុគ្គលិក។ អ្នកមាន `Employee` ជា Base Class ហើយមាន `Manager`, `Developer`, `Guard` ជា Derived Classes។ គ្រប់គ្នាទារប្រាក់ខែដូចគ្នា (ហៅ Method `CalculateSalary()`) តែរូបមន្តគណនាប្រាក់ខែពួកគេម្នាក់ៗគឺខុសគ្នា។
* **បើគ្មានវាទេ៖** ពេលចង់បើកប្រាក់ខែឱ្យបុគ្គលិកទាំងអស់ អ្នកត្រូវសរសេរ `if` ច្រើនមែនទែន៖
```csharp
if (emp is Manager) { /* គណនារបៀបអ្នកគ្រប់គ្រង */ }
else if (emp is Developer) { /* គណនារបៀបអ្នកសរសេរកូដ */ }

```


* **ពេលមានវា (Dynamic Binding):** អ្នកគ្រាន់តែប្រកាស Method `CalculateSalary()` ជា `virtual` ក្នុង Employee ហើយឱ្យ Class កូនៗនីមួយៗ `override` វា។ ពេលចង់បើកលុយ អ្នកគ្រាន់តែប្រើ Loop ខ្លីមួយ៖
```csharp
// Array នេះផ្ទុកទាំង Manager, Developer និង Guard ចម្រុះគ្នា
foreach (Employee emp in employeeList) 
{
    // កម្មវិធីនឹងមើលវត្ថុជាក់ស្ដែងនៅពេល Run (Run-time)
    // បើវត្ថុនោះជា Manager វានឹងរត់ទៅរកកូដក្នុង Manager, បើជា Developer រត់ទៅរក Developer 
    emp.CalculateSalary(); 
}

```



### សរុបជារួម៖

* **Overloading (Compile-time):** ដោះស្រាយបញ្ហា **"សកម្មភាពតែមួយ តែទទួលទិន្នន័យចូលខុសគ្នា"**។ ជួយឱ្យកូដស្អាត ងាយស្រួលហៅប្រើ។
* **Overriding (Run-time):** ដោះស្រាយបញ្ហា **"បញ្ជាតែមួយ តែអ្នកអនុវត្តមានអត្តសញ្ញាណខុសគ្នា ត្រូវធ្វើការងារខុសគ្នា"**។ ជួយឱ្យប្រព័ន្ធមានភាពបត់បែន ងាយស្រួលថែម Class ថ្មីៗទៅថ្ងៃក្រោយដោយមិនបាច់កែកូដចាស់។

---

## ចូររៀបរាប់អំពីអត្ថប្រយោជន៍នៃ OOP។
ខាងក្រោមនេះជាអត្ថប្រយោជន៍សំខាន់ៗរបស់ OOP៖

**១. ការប្រើប្រាស់កូដឡើងវិញ (Reusability)**  
អាចប្រើកូដដែលមានស្រាប់ឡើងវិញតាមរយៈការទទួលមរតក (Inheritance) និងសមាសភាព (Composition) ជួយសន្សំពេលវេលា និងកាត់បន្ថយការសរសេរកូដដដែលៗ (DRY)។

**២. ការបិទបាំង និងការពារទិន្នន័យ (Encapsulation & Data Hiding)**  
ប្រើ Access Modifiers (`private`, `protected`, `public`) ដើម្បីលាក់ព័ត៌មានលម្អិតខាងក្នុង ការពារទិន្នន័យមិនឱ្យត្រូវបានកែប្រែដោយផ្ទាល់ពីខាងក្រៅ បង្កើនសុវត្ថិភាពកម្មវិធី។

**៣. ការលាក់បាំងភាពស្មុគស្មាញ (Abstraction)**  
បង្ហាញតែចំណុចប្រទាក់ (Interface) សំខាន់ៗដល់អ្នកប្រើប្រាស់ ដោយលាក់ដំណើរការខាងក្នុងដែលស្មុគស្មាញ ធ្វើឱ្យអ្នកប្រើប្រាស់ងាយស្រួលប្រើប្រាស់វត្ថុ (Object) ដោយមិនចាំបាច់យល់ពីកូដខាងក្នុង។

**៤. ភាពបត់បែនតាមរយៈពហុរូបភាព (Polymorphism)**  
វត្ថុផ្សេងគ្នាអាចឆ្លើយតបទៅនឹងការហៅមុខងារដូចគ្នា ប៉ុន្តែមានឥរិយាបទខុសៗគ្នា (Method Overriding/Overloading) ធ្វើឱ្យកូដមានភាពយឺតយ៉ាវ និងងាយស្រួលក្នុងការគ្រប់គ្រង។

**៥. សមត្ថភាពពង្រីកប្រព័ន្ធដោយមិនប៉ះកូដចាស់ (Extensibility)**  
អនុញ្ញាតឱ្យបន្ថែមមុខងារថ្មីៗទៅក្នុងប្រព័ន្ធ ដោយមិនចាំបាច់កែប្រែកូដចាស់ដែលមានស្រាប់ (ប្រកាន់ខ្ជាប់គោលការណ៍ Open/Closed) កាត់បន្ថយហានិភ័យនៃការបង្កើតកំហុសថ្មី។

**៦. ងាយស្រួលក្នុងការថែទាំរយៈពេលវែង (Maintainability)**  
កូដត្រូវបានបែងចែកជាម៉ូឌុល (Modularity) និងថ្នាក់ (Class) នីមួយៗដើរតួជាប្រអប់ខ្មៅ (Black Box) ដាច់ដោយឡែក ធ្វើឱ្យការកែប្រែ ឬបន្ថែមមុខងារនាពេលអនាគតមានភាពងាយស្រួល។

**៧. ងាយស្រួលក្នុងការតាមដាន និងជួសជុលកំហុស (Debugging)**  
ដោយសារថ្នាក់នីមួយៗឯករាជ្យពីគ្នា ពេលមានកំហុសកើតឡើង អ្នកអភិវឌ្ឍន៍អាចផ្តោតស៊ើបអង្កេតលើថ្នាក់ជាក់លាក់ណាមួយ ដោយមិនប៉ះពាល់ដល់ផ្នែកផ្សេងទៀត ធ្វើឱ្យការជួសជុលកាន់តែលឿន និងមានប្រសិទ្ធភាព។

**៨. ឆ្លុះបញ្ចាំងពីបញ្ហាក្នុងពិភពពិត (Real-world Modeling)**  
ប្រើគំនិត "វត្ថុ" (Objects) ដែលមានទាំងទិន្នន័យ (Attributes) និងឥរិយាបទ (Methods) ធ្វើឱ្យការរៀបចំផែនការ និងការសរសេរកូដជិតស្និទ្ធនឹងជីវិតប្រចាំថ្ងៃ (ឧ. រថយន្ត បុគ្គលិក) ងាយយល់សម្រាប់អ្នកថ្មី និងងាយទំនាក់ទំនងក្នុងក្រុមការងារ។

**៩. បង្កើនល្បឿននៃការអភិវឌ្ឍន៍ (Productivity)**  
ដោយសារមានបណ្ណាល័យ (Libraries) និង Framework ជាច្រើនដែលសាងសង់តាម OOP អ្នកអភិវឌ្ឍន៍អាចផ្តោតលើតក្កវិជ្ជាអាជីវកម្មស្នូល (Business Logic) ជំនួសឱ្យការបង្កើតរចនាសម្ព័ន្ធមូលដ្ឋានពីដំបូង ធ្វើឱ្យការងារលឿនជាងមុន។

**១០. គាំទ្រដល់ការអភិវឌ្ឍន៍ស្របគ្នាក្នុងក្រុម (Parallel Development)**  
ដោយសារថ្នាក់នីមួយៗមានភាពឯករាជ្យ អ្នកអភិវឌ្ឍន៍ច្រើននាក់អាចធ្វើការលើថ្នាក់ផ្សេងៗគ្នាក្នុងពេលតែមួយ ដោយមិនសូវមានការប៉ះទង្គិចគ្នា (Merge Conflict) ធ្វើឱ្យក្រុមការងារធំៗអាចសហការគ្នាបានយ៉ាងមានប្រសិទ្ធភាព។

---

**សេចក្តីសន្និដ្ឋានជារួម៖**  
ទោះបី OOP ពិបាករៀននៅដំណាក់កាលដំបូងក៏ដោយ ប៉ុន្តែចំណុចទាំង ១០ ខាងលើនេះបង្ហាញថា វាជាគំរូសរសេរកម្មវិធី (Paradigm) ដ៏ល្អបំផុតសម្រាប់គ្រប់គ្រងភាពស្មុគស្មាញ កាត់បន្ថយថ្លៃថែទាំរយៈពេលវែង និងបង្កើនសមត្ថភាពពង្រីកប្រព័ន្ធ ជាពិសេសសម្រាប់កម្មវិធីទំនើបៗដូចជា កម្មវិធីទូរស័ព្ទ ហ្គេម និងប្រព័ន្ធគ្រប់គ្រងសហគ្រាស។

---
*ចប់មេរៀន*