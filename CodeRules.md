Naming Conventions based on https://www.dofactory.com/csharp-coding-standards

Formatting Conventions based on VS settings and my personal preferences

# C# Coding Standards and Best Practices
## Naming Conventions
### Class Names

`DO` use PascalCasing for class names and method names.
```C#
public class ClientActivity {
    public void ClearStatistics() {
        //...
    }
    public void CalculateStatistics() {
        //...
    }
}
```

### Variable Names
`DO` use camelCasing for local variables and method arguments.
```C#
public class UserLog {
    public void Add(LogEvent logEvent) {
        int itemCount = logEvent.Items.Count;
        // ...
    }
}
```
`DO NOT` use Hungarian notation or any other type identification in identifiers.
```C#
// Correct
int counter;
string name;
 
// Avoid
int iCounter;
string strName;
```

### Constants
Need to discuss. The original document stands for:

`DO NOT` use Screaming Caps for constants or readonly variables.
```C#
// Correct
public static const string ShippingType = "DropShip";
 
// Avoid
public static const string SHIPPINGTYPE = "DropShip";
```
Personally I like to use capitalized constants names with words separated with `_`:
```C#
public static const string SHIPPING_TYPE = "DropShip";
```

### Abbreviations
`AVOID` using Abbreviations.

Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri
```C#
// Correct
UserGroup userGroup;
Assignment employeeAssignment;
 
// Avoid
UserGroup usrGrp;
Assignment empAssignment;
 
// Exceptions
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
UriPart uriPart;
```
`DO` use PascalCasing for abbreviations 3 characters or more (2 chars are both uppercase).
```C#
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer;
UIControl uiControl;
```

### No Underscores
`DO NOT` use Underscores in identifiers.

Exception: you can prefix private static variables with an underscore.

Exception (personally from me, argueable): you can use underscores in capitalized constants names as `const int MAX_INTEGER_VALUE = 100`
```C#
// Correct
public DateTime clientAppointment;
public TimeSpan timeLeft;
 
// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left;
 
// Exception
private DateTime _registrationDate;
```

### Type Names
`DO USE` predefined type names instead of system type names like Int16, Single, UInt64, etc.
```C#
// Correct
string firstName;
int lastIndex;
bool isSaved;
 
// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
```

### Implicit Types
`DO USE` implicit type var for local variable declarations.

Exception: primitive types (int, string, double, etc) use predefined names.
```C#
var stream = File.Create(path);
var customers = new Dictionary();
 
// Exceptions
int index = 100;
string timeSheet;
bool isCompleted;
```

### Noun Class Names
`DO USE` noun or noun phrases to name a class.

```C#
public class Employee {
}

public class BusinessLocation {

}
public class DocumentCollection {
}

```

## Interfaces
`DP` prefix interfaces with the letter I.  Interface names are noun (phrases) or adjectives.
```C#
public interface IShape {
}

public interface IShapeCollection {
}

public interface IGroupable {
}
```

### Curly Brackets
`DO NOT` vertically align curly brackets.

```C#
// Incorrect
class Program
{
    static void Main(string[] args)
    {
    }
}

// Correct
class Program {
    static void Main(string[] args) {
    }
}
```

### Member variables
`DO` declare all member variables at the top of a class, with static variables at the very top (need to check this statement with current approach).
```C#
// Correct
public class Account {
    public static string BankName;
    public static decimal Reserves;
 
    public string Number { get; set; }
    public DateTime DateOpened { get; set; }
    public DateTime DateClosed { get; set; }
    public decimal Balance { get; set; }
 
    // Constructor
    public Account() {
        // ...
    }
}
```
## Formatting Conventions
### Place open brace on new line for types `VS` `uncheck`
```C#
// Correct
class C {
}

// Incorrect
class C
{
}
```
### Place open brace on new line for methods and local functions `VS` `uncheck`
```C#
// Correct
void Goo() {
    Console.WriteLine();

    int LocalFunction(int x) {
        return 2 * x;
    }

    Console.ReadLine();
}

// Incorrect
void Goo()
{
    Console.WriteLine();

    int LocalFunction(int x)
    {
        return 2 * x;
    }

    Console.ReadLine();
}
```

### Place open brace on new line for properties, indexers and events `VS` `uncheck`
```C#
// Correct
public int Property {
    ...
}

// Incorrect
public int Property
{
    ...
}
```

### Place open brace on new line for property, indexer and event accessors `VS` `uncheck`
```C#
// Correct
public int Property {
    get {
        return 42;
    }
}

// Incorrect
public int Property {
    get
    {
        return 42;
    }
}
```

### Place open brace on new line for anonymous methods `VS` `uncheck`
```C#
// Correct
D d = delegate (int x) {
    return 2 * x;
}

// Incorrect
D d = delegate (int x)
{
    return 2 * x;
}
```

### Place open brace on new line for control blocks `VS` `uncheck`
```C#
// Correct
for (int i; i < 10; i++) {
}

// Incorrect
for (int i; i < 10; i++)
{
}
```

### Place open brace on new line for anonymous types `VS` `uncheck`
```C#
// Correct
var z = new {
    A = 3,
    B = 4
}

// Incorrect
var z = new
{
    A = 3,
    B = 4
}
```

### Place open brace on new line for object, collection, array, and with initializers `VS` `uncheck`
```C#
// Correct
var z = new B() {
    A = 3,
    B = 4
};

var collectionVariable = new List<int> {
}

var arrayVariable = new int[] {
}

// Incorrect
var z = new B()
{
    A = 3,
    B = 4
};

var collectionVariable = new List<int>
{
}

var arrayVariable = new int[]
{
}
```

### Place open brace on new line for lambda expression `VS` `uncheck`
```C#
// Correct
Func<int, int> f = x => {
    return 2 * x;
};

// Incorrect
Func<int, int> f = x =>
{
    return 2 * x;
};
```

### [Place "else" on new line `VS` `check`
```C#
// Incorrect
if (false) {
} else {
}

// Incorrect
if (false) {
}
else {
}

```

### Place "catch" and "finally" on new line `VS` `check`
```C#
// Correct
try {
}
catch (Exception e) {
}
finally {
}

// Incorrect
try {
} catch (Exception e) {
} finally {
}
```

### Place members in object initializers on new line `VS` `check`
```C#
// Correct
var z = new B() {
    A = 3,
    B = 4
}

// Incorrect
var z = new B() {
    A = 3, B = 4
}
```

### Place members in anonymous types on new line `VS` `check`
```C#
// Correct
var z = new {
    A = 3,
    B = 4
}

// Incorrect
var z = new {
    A = 3, B = 4
}
```

### Place query expression clauses on new line `VS` `uncheck`
```C#
// Correct
var q = from a in e
        from b in e
        select a * b;

// Incorrect
var q = from a in e from b in e
        select a * b;
```
### VS Settings screenshots
![image](https://github.com/AlexKamaev/issues/assets/1678902/9ec11da3-6f26-41da-9891-d390748c2db6)

