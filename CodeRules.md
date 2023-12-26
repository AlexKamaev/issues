Naming Conventions based on https://www.dofactory.com/csharp-coding-standards

Formatting Conventions based on VS settings and my personal preferences

TODO: Need to consider these existing rules in the future: http://wiki.pages.devx/blazorwiki/squads/grid/

TODO: Consider these great docs as well:

- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions
- https://google.github.io/styleguide/csharp-style.html

# C# Coding Standards and Best Practices
## Naming Conventions
### Class Names

:ballot_box_with_check: use PascalCasing for class names and method names.
```C#
public class ClientActivity {
    public void ClearStatistics () {
        //...
    }
    public void CalculateStatistics () {
        //...
    }
}
```

### Variable Names
:ballot_box_with_check: use camelCasing for local variables and method arguments.
```C#
public class UserLog {
    public void Add (LogEvent logEvent) {
        int itemCount = logEvent.Items.Count;
        // ...
    }
}
```
:x: do not use Hungarian notation or any other type identification in identifiers.
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

:x: do not use Screaming Caps for constants or readonly variables.
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
:x: avoid using Abbreviations.

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
:ballot_box_with_check: use PascalCasing for abbreviations 3 characters or more (2 chars are both uppercase).
```C#
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer;
UIControl uiControl;
```

### No Underscores
:x: do not use Underscores in identifiers.

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
:ballot_box_with_check: use predefined type names instead of system type names like Int16, Single, UInt64, etc.
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
:ballot_box_with_check: use implicit type var for local variable declarations.

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
:ballot_box_with_check: use noun or noun phrases to name a class.

```C#
public class Employee {
}

public class BusinessLocation {

}
public class DocumentCollection {
}

```

## Interfaces
:ballot_box_with_check: use prefix interfaces with the letter I.  Interface names are noun (phrases) or adjectives.
```C#
public interface IShape {
}

public interface IShapeCollection {
}

public interface IGroupable {
}
```

### Curly Brackets
:x: do not vertically align curly brackets.

```C#
// Incorrect
class Program
{
    static void Main (string[] args)
    {
    }
}

// Correct
class Program {
    static void Main (string[] args) {
    }
}
```

### Member variables
:ballot_box_with_check: declare all member variables at the top of a class, with static variables at the very top (need to check this statement with current approach).
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
    public Account () {
        // ...
    }
}
```
## Formatting Conventions - Indentation
### :ballot_box_with_check: Indent block contents `VS`
```C#
// four whitespaces not tab
// Correct
int Method () {
    int x;
    int y;
}

// Incorrect
int Method () {
int x;
int y;
}

```

### :x: Indent open and close braces `VS`
```C#
// Correct
int Method () {
    int x;
    int y;
}

// Incorrect
int Method () {
    int x;
    int y;
    }
```
### :ballot_box_with_check: Indent case content `VS`
### :x: Indent case content (when block) `VS`
### :ballot_box_with_check: Indent case labels `VS`

```C#
switch (goo) {
    case 1: {
        break;
    }
    case 2:
        break;
}
```

### VS Screenshots
![image](https://github.com/AlexKamaev/issues/assets/1678902/8100539c-556d-46f2-968b-4f379e4c1b65)


## Formatting Conventions - New Lines
### :x: Place open brace on new line for types `VS`
```C#
// Correct
class C {
}

// Incorrect
class C
{
}
```
### :x: Place open brace on new line for methods and local functions `VS`
```C#
// Correct
void Goo() {
    Console.WriteLine();

    int LocalFunction (int x) {
        return 2 * x;
    }

    Console.ReadLine();
}

// Incorrect
void Goo()
{
    Console.WriteLine();

    int LocalFunction (int x)
    {
        return 2 * x;
    }

    Console.ReadLine();
}
```

### :x: Place open brace on new line for properties, indexers and events `VS`
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

### :x: Place open brace on new line for property, indexer and event accessors `VS`
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

### :x: Place open brace on new line for anonymous methods `VS`
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

### :x: Place open brace on new line for control blocks `VS`
```C#
// Correct
for (int i; i < 10; i++) {
}

// Incorrect
for (int i; i < 10; i++)
{
}
```

### :x: Place open brace on new line for anonymous types `VS`
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

### :x: Place open brace on new line for object, collection, array, and with initializers `VS`
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

### :x: Place open brace on new line for lambda expression `VS`
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

### :ballot_box_with_check: Place "else" on new line `VS`
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

### :ballot_box_with_check: Place "catch" and "finally" on new line `VS`
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

### :ballot_box_with_check: Place members in object initializers on new line `VS`
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

### :ballot_box_with_check: Place members in anonymous types on new line `VS`
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

### :ballot_box_with_check: Place query expression clauses on new line `VS`
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

## Formatting Conventions - Spacing
### :ballot_box_with_check: Insert space between method name and its opening parenthesis `VS`
### :x: Insert space within parameter list parentheses `VS`
### :x: Insert space within empty parameter list parentheses `VS`

### :x: Insert space between called method name and its opening parentheses `VS`
### :x: Insert space withing argument lsit parentheses `VS`
### :x: Insert space within empty argument list parentheses `VS`

```C#
void Goo () {
    Goo(1);
}

void Goo (int x) {
    Goo();
}
```

### :ballot_box_with_check: Insert space after keywords in control flow statements `VS`
```C#
// Correct
for (int i; i < x; i++) {
}

// Incorrect
for(int i; i < x; i++) {
}
```
### :x: Insert space within parentheses of expressions `VS`
```C#
// Correct
var z = (x * y) - ((y - x) * 3);

// Incorrect
var z = ( x * y ) - ( ( y - x ) * 3 );
```
### :x: Insert space within parentheses of type casts `VS`
```C#
// Correct
int y = (int)x;

// Incorrect
int y = ( int )x;
```
### :x: Insert spaces within parentheses of control flow statements `VS`
```C#
// Correct
for (int i; i < x; i++) {
}

// Incorrect
for ( int i; i < x; i++ ) {
}
```
### :x: Insert space after cast `VS`
```C#
// Correct
int y = (int)x;

// Incorrect
int y = (int) x;
```
### Ignore spaces in declaration statements `VS` :x:
```C#
// However, I would like to enable this option
// Correct
int index = 0;
string text = "Start";

// Incorrect
int    index = 0;
string text = "Start";
```
### :x: Insert space before open square bracket
### :x: Insert space within empty square brackets
### :x: Insert spaces within square brackets
```C#
// Correct
int[] x = new int[10];

// Incorrect
int [ ] = new int [ 10 ];
```
### :ballot_box_with_check: Insert space after colon for base or interface in type declaration
```C#
// Correct
class C : I

// Incorrect
class C :I
```
### :ballot_box_with_check: Insert space after comma
```C#
// Correct
this.Goo(x, y);

// Incorrect
this.Goo(x,y);
```
### :x: Insert space after dot
```C#
// Correct
this.Goo(x, y);

// Incorrect
this. Goo(x,y);
```
### :ballot_box_with_check: Insert space after semicolon in "for" statement
```C#
// Correct
for (int i; i < x; i++)

// Incorrect
for (int i;i < x;i++)
```

### :ballot_box_with_check: Insert space before colon for base or interface in type declaration
```C#
// Correct
class C : I

// Incorrect
class C: I
```
### :x: Insert space before comma
```C#
// Correct
this.Goo(x, y);

// Incorrect
this.Goo(x , y);
```
### :x: Insert space before dot
```C#
// Correct
this.Goo(x, y);

// Incorrect
this .Goo(x , y);
```
### :x: Insert space before semicolon in "for" statement
```C#
// Correct
for (int i; i < x; i++)

// Incorrect
for (int i ; i < x ; i++)
```
### :ballot_box_with_check: Insert space before and after binary operators
```C#
return x * (x - y);
```

### VS Settings Screenshots
![image](https://github.com/AlexKamaev/issues/assets/1678902/8ff583b8-7e99-4084-b439-7dc0dbfcb19e)


## Formatting Conventions - Wrapping

### :ballot_box_with_check: Leave block on single line
```C#
public int Goo { get; set; }
```
### :x: Leave statements and member declarations on the same line
```C#
// Correct
int i = 0;
string name = "Jonh"

// Incorrect
int i = 0; string name = "Jonh"
```
## Editor Config for `.cs` files
```
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = none
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = false
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = true
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = false
csharp_preserve_single_line_statements = false

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = error
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i
```
## Personal style preferences. Cannot set up `dotnet format` for these purposes =(
### :ballot_box_with_check: add an empty line before/after variable declarations and assignements
```C#
int a = 0;
int b = 1;

Console.WriteLine(0);
```
### :ballot_box_with_check: add an empty line before/after block (for, while, if, else, try, catch, etc) section
```C#
if (true) {
    Console.WriteLine(1);
    Console.WriteLine(2);
}

Console.WriteLine(3);
```
### :ballot_box_with_check: add an empty line between properties and methods
```C#
    public int Number () {
        get; set;
    }

    public void Method1 () {
        ...
    }

    public void Method2 () {
        ...
    }
```

### :ballot_box_with_check: remove unused usings

## Formatted code example
```C#
using System;

public interface IMyInterfacable {
    string Name {
        get; set;
    }
}

public class A {
    int id;
    string name;

    public A () {
        id = 1;
        name = "a";

        DoNothing();
    }

    public void DoNothing () {
    }
}

class B : A {
    const int MaxIntergerValue = 10;
}

public class Class1 {
    public Class1 () {
    }

    public void ForLoop () {
        for (int i = 0; i < 100; i++) {
            Console.WriteLine(i);
        }

    }

    public void SwitchStatement (bool p) {
        switch (p) {
            case true:
                return;
            case false:
                return;
        }
    }

    public void TryCatch () {
        try {
            throw new Exception();
        }
        catch (Exception e) {
            Console.WriteLine("exception");
        }
        finally {
            // Do cleanup
        }
    }

    public void IfElse (bool p) {
        if (p) {
            Console.WriteLine(true);
        }
        else {
            Console.WriteLine(false);
        }
    }
}
```
