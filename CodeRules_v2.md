# C# Naming rules and conventions
## Code:
- Use noun or noun phrases to name a class
- Use meaningful and descriptive names for variables, methods, and classes
- Prefer clarity over brevity
- Names of classes, methods, enumerations, public fields, public properties, namespaces: `PascalCase`
- Names of local variables, parameters: `camelCase`
- Names of private, protected, internal and protected internal fields and properties: `camelCase`
- Names of interfaces start with I, e.g. IInterface
- Names of type parameters start with T, e.g. ITypeParameter
- Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri
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

namespace MyNamespace {
    public interface IMyInterface {
        public int Calculate (float value, float exp);
    }

    public enum MyEnum {
        Yes,
        No,
    }

    public class MyClass {
        public int Foo = 0;
        public bool NoCounting = false;

        private class Results {
            public int NumNegativeResults = 0;
            public int NumPositiveResults = 0;
        }

        private Results results;
        private const int Bar = 100;

        public static int NumTimesCalled = 0;

        public MyClass () {
            this._results = new Results { NumNegativeResults = 1, NumPositiveResults = 1, };
        }

        public int CalculateValue (int mulNumber) {
            var resultValue = this.Foo * mulNumber;

            NumTimesCalled++;

            this.Foo += _bar;

            if (!this.NoCounting) {
                if (resultValue < 0)
                    this._results.NumNegativeResults++;
                else
                    this._results.NumPositiveResults++;
            }

            return resultValue;
        }

        public void ExpressionBodies () {
            Func<int, int> increment = x => x + 1;

            Func<int, int, long> difference1 = (x, y) => {
                long diff = (long)x - y;

                return diff >= 0 ? diff : -diff;
            };

            Func<int, int, long> difference2 =
                (x, y) => {
                    long diff = (long)x - y;

                    return diff >= 0 ? diff : -diff;
                };

            CallWithDelegate(
                (x, y) => {
                    long diff = (long)x - y;

                    return diff >= 0 ? diff : -diff;
                });
        }

        void DoNothing () { }

        void AVeryLongFunctionNameThatCausesLineWrappingProblems (
            int longArgumentName,
            int p1,
            int p2
        ) {
        }

        void AnotherLongFunctionNameThatCausesLineWrappingProblems (
            int longArgumentName, int longArgumentName2, int longArgumentName3) {
        }

        void CallingLongFunctionName () {
            int veryLongArgumentName = 1234;
            int shortArg = 1;

            this.AnotherLongFunctionNameThatCausesLineWrappingProblems(
                shortArg,
                shortArg,
                veryLongArgumentName
            );

            this.AnotherLongFunctionNameThatCausesLineWrappingProblems(
                veryLongArgumentName,
                veryLongArgumentName,
                veryLongArgumentName
            );
        }
    }
}
```
 
