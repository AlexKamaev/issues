copyied from https://www.dofactory.com/csharp-coding-standards

# C# Coding Standards and Best Practices
## Class Names

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

## Variable Names
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

## Constants
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

## Abbreviations
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

## No Underscores
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

## Type Names
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

## Implicit Types
`DO USE` implicit type var for local variable declarations.

Exception: primitive types (int, string, double, etc) use predefined names.
```CS
var stream = File.Create(path);
var customers = new Dictionary();
 
// Exceptions
int index = 100;
string timeSheet;
bool isCompleted;
```

## Noun Class Names
`DO USE` noun or noun phrases to name a class.

```CS
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

## Curly Brackets
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

## Member variables
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
