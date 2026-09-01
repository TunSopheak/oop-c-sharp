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

*ចប់មេរៀន*