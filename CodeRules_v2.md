# C# Naming rules and conventions
## Naming
- Use noun or noun phrases to name a class
- Use meaningful and descriptive names for variables, methods, and classes
- Prefer clarity over brevity
- Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri
- Do not use Hungarian notation or any other type identification in names
#### Names formatting
- Names of classes, methods, enumerations, public fields, public properties, namespaces: `PascalCase`
- Names of local variables, parameters: `camelCase`
- Names of private, protected, internal and protected internal fields and properties: `camelCase`
- Names of interfaces start with I, e.g. IInterface
- Names of type parameters start with T, e.g. ITypeParameter
## Coding conventions:
- Use `this` to access fields, properties, methods in currect class
- Use of `var` is encouraged if it aids readability by avoiding type names that are noisy, obvious, or unimportant.
  - Encouraged:
    - When the type is obvious - e.g. var apple = new Apple();, or var request = Factory.Create<HttpRequest>();
    - For transient variables that are only passed directly to other methods - e.g. var item = GetItem(); ProcessItem(item);
  - Discouraged:
    - When working with basic types - e.g. var success = true;
    - When working with compiler-resolved built-in numeric types - e.g. var number = 12 * ReturnsFloat();
    - When users would clearly benefit from knowing the type - e.g. var listOfItems = GetList();
- Attributes
  - Attributes should appear on the line above the field, property, or method they are associated with, separated from the member by a newline.
  - Multiple attributes should be separated by newlines. This allows for easier adding and removing of attributes, and ensures each attribute is easy to search for.  

## File:
- Filenames and directory names are PascalCase, e.g. MyFile.cs.
- Where possible the file name should be the same as the name of the main class in the file, e.g. MyClass.cs
- In general, prefer one core class per file

## Organization:
- Modifiers occur in the following order: public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async
- Namespace using declarations go at the top, before any namespaces. using import order is alphabetical, apart from System imports which always go first
- Class member ordering:
  - Group class members in the following order:
    - Nested classes, enums, delegates and events
    - Static, const and readonly fields
    - Fields and properties
    - Constructors and finalizers
    - Methods
  - Within each group, elements should be in the following order:
    - Public
    - Internal
    - Protected internal
    - Protected
    - Private
  - Where possible, group interface implementations together

## Formatting
- A maximum of one statement per line
- A maximum of one assignment per statement
- Indentation of 4 spaces, no tabs
- No line break before opening brace
- Line break between closing brace and else
- Line break after every block statement (if, for, etc)
- Line break after variable declaration section or assignment section
- Line break after multiline property declarations, classes, enums, methods, etc
- Braces can be ignored when optional
- Space after if/for/while etc., and after commas
- Space after function name in function declaration, no space in function call
- No space after an opening parenthesis or before a closing parenthesis
- No space between a unary operator and its operand. One space between the operator and each operand of all other operators

```C#
using System;

public namespace MyNamespace {
    public interface IMyInterfacable {
        string Name { get; set; }
    }

    public class A {
        int id = 4;
        string name = "";

        public static int StaticFn () {
            Console.WriteLine("test");

            return 1;
        }

        public A () {
            this.id = 1;
            this.name = "a";

            StaticFn();
        }
    }

    class B : A {
        const int MaxIntergerValue = 10;
        const int MinIntegerValue = 1;
    }

    public class Class1 {
        public Class1 () {
        }

        public void ForLoop<TTypeParam> () {
            int q = 10;

            for (int i = 0; i < 100; i++) {
                Console.WriteLine(i);
            }
        }

        public void NotCapitalizedMethod () {
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
                Console.WriteLine(e.Message);
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
            else
                Console.WriteLine(false);
        }
    }
}
```
# VS Studio settings
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

public int Property { get { return 42; } }

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

# Organize usings
dotnet_sort_system_directives_first = true

## Modifier order
csharp_preferred_modifier_order = public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:error

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

# this. preferences
dotnet_style_qualification_for_field = true:error
dotnet_style_qualification_for_property = true:error
dotnet_style_qualification_for_method = true:error
dotnet_style_qualification_for_event = true:error

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
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = false

# Naming rules
dotnet_naming_symbols.non_locals.applicable_kinds = namespace, class, struct, interface, enum, property, method, event, delegate, type_parameter, local_function
dotnet_naming_symbols.non_locals.applicable_accessibilities = *

dotnet_naming_symbols.locals.applicable_kinds = field, parameter
dotnet_naming_symbols.locals.applicable_accessibilities = private

dotnet_naming_symbols.constant_fields.applicable_kinds = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities = *
dotnet_naming_symbols.constant_fields.required_modifiers = const

dotnet_naming_symbols.interfaces.applicable_kinds = interface

dotnet_naming_symbols.type_parameters.applicable_kinds = type_parameter

dotnet_naming_style.pascal_case_style.capitalization = pascal_case
dotnet_naming_style.camel_case_style.capitalization = camel_case
dotnet_naming_style.begins_with_I.capitalization = pascal_case
dotnet_naming_style.begins_with_I.required_prefix = I
dotnet_naming_style.begins_with_T.capitalization = pascal_case
dotnet_naming_style.begins_with_T.required_prefix = T

dotnet_naming_rule.non_locals_must_be_in_pascal_case.symbols = non_locals
dotnet_naming_rule.non_locals_must_be_in_pascal_case.style = pascal_case_style
dotnet_naming_rule.non_locals_must_be_in_pascal_case.severity = error

dotnet_naming_rule.locals_must_be_in_camel_case.symbols = locals
dotnet_naming_rule.locals_must_be_in_camel_case.style = camel_case_style
dotnet_naming_rule.locals_must_be_in_camel_case.severity = error

dotnet_naming_rule.constant_fields_must_be_in_pascal_case.symbols = constant_fields
dotnet_naming_rule.constant_fields_must_be_in_pascal_case.style = pascal_case_style
dotnet_naming_rule.constant_fields_must_be_in_pascal_case.severity = error

dotnet_naming_rule.interfaces_must_begin_with_i.symbols = interfaces
dotnet_naming_rule.interfaces_must_begin_with_i.style = begins_with_I
dotnet_naming_rule.interfaces_must_begin_with_i.severity = error

dotnet_naming_rule.type_parameters_must_begin_with_t.symbols = type_parameters
dotnet_naming_rule.type_parameters_must_begin_with_t.style = begins_with_T
dotnet_naming_rule.type_parameters_must_begin_with_t.severity = error
```
 
