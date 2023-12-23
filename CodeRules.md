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
