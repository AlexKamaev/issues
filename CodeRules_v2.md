# C# Naming rules and conventions
## Code:
- Names of classes, methods, enumerations, public fields, public properties, namespaces: `PascalCase`
- Names of local variables, parameters: `camelCase`
- Names of private, protected, internal and protected internal fields and properties: `camelCase`
- Names of interfaces start with I, e.g. IInterface
- Names of type parameters start with T, e.g. ITypeParameter

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
- Braces can be ignored when optional
- Space after if/for/while etc., and after commas
- Space after function name in function declaration, no space in function call
- No space after an opening parenthesis or before a closing parenthesis
- No space between a unary operator and its operand. One space between the operator and each operand of all other operators
 
