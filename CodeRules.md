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
## Formatting Conventions - Indentation
### Indent block contents `VS` `check`
```C#
// four whitespaces not tab
int Method() {
    int x;
    int y;
}
```

### Indent open and close braces `VS` `uncheck`
```C#
int Method() {
    int x;
    int y;
}
```
### Indent case content `VS` `check`
### Indent case content (when block) `VS` `uncheck`
### Indent case labels `VS` `check`

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

### Place "else" on new line `VS` `check`
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

## Formatting Conventions - Spacing
### Insert space between method name and its opening parenthesis `VS` `check`
### Insert space within parameter list parentheses `VS` `uncheck`
### Insert space within empty parameter list parentheses `VS` `uncheck`

### Insert space between called method name and its opening parentheses `VS` `uncheck`
### Insert space withing argument lsit parentheses `VS` `uncheck`
### Insert space within empty argument list parentheses `VS` `uncheck`

```C#
void Goo () {
    Goo(1);
}

void Goo (int x) {
    Goo();
}
```

### Insert space after keywords in control flow statements `VS` `check`
```C#
// Correct
for (int i; i < x; i++) {
}

// Incorrect
for(int i; i < x; i++) {
}
```
### Insert space within parentheses of expressions `VS` `uncheck`
```C#
// Correct
var z = (x * y) - ((y - x) * 3);

// Incorrect
var z = ( x * y ) - ( ( y - x ) * 3 );
```
### Insert space within parentheses of type casts `VS` `uncheck`
```C#
// Correct
int y = (int)x;

// Incorrect
int y = ( int )x;
```
### Insert spaces within parentheses of control flow statements `VS` `uncheck`
```C#
// Correct
for (int i; i < x; i++) {
}

// Incorrect
for ( int i; i < x; i++ ) {
}
```
### Insert space after cast `VS` `uncheck`
```C#
// Correct
int y = (int)x;

// Incorrect
int y = (int) x;
```
### Ignore spaces in declaration statements `VS` `uncheck`
```C#
// However, I would like to enable this option
// Correct
int index = 0;
string text = "Start";

// Incorrect
int    index = 0;
string text = "Start";
```
### 𐄂 Insert space before open square bracket
### 𐄂 Insert space within empty square brackets
### 𐄂 Insert spaces within square brackets
```C#
// Correct
int[] x = new int[10];

// Incorrect
int [ ] = new int [ 10 ];
```
### ✔ Insert space after colon for base or interface in type declaration
```C#
// Correct
class C : I

// Incorrect
class C :I
```
### ✔ Insert space after comma
```C#
// Correct
this.Goo(x, y);

// Incorrect
this.Goo(x,y);
```
### 𐄂 Insert space after dot
```C#
// Correct
this.Goo(x, y);

// Incorrect
this. Goo(x,y);
```
### ✔ Insert space after semicolon in "for" statement
```C#
// Correct
for (int i; i < x; i++)

// Incorrect
for (int i;i < x;i++)
```

### ✔ Insert space before colon for base or interface in type declaration
```C#
// Correct
class C : I

// Incorrect
class C: I
```
### 𐄂 Insert space before comma
```C#
// Correct
this.Goo(x, y);

// Incorrect
this.Goo(x , y);
```
### 𐄂 Insert space before dot
```C#
// Correct
this.Goo(x, y);

// Incorrect
this .Goo(x , y);
```
### 𐄂 Insert space before semicolon in "for" statement
```C#
// Correct
for (int i; i < x; i++)

// Incorrect
for (int i ; i < x ; i++)
```
### ✔ Insert space before and after binary operators
```C#
return x * (x - y);
```

### VS Settings Screenshots
![image](https://github.com/AlexKamaev/issues/assets/1678902/8ff583b8-7e99-4084-b439-7dc0dbfcb19e)


## Formatting Conventions - Wrapping

### ✔ Leave block on single line
```C#
public int Goo { get; set; }
```
### 𐄂 Leave statements and member declarations on the same line
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
