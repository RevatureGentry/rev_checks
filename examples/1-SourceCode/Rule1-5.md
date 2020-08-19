# Rule 1.5 - Non-empty blocks use K&R Egyptian Style Curly Brackets
### Example
```java
package com.revaturelabs;

public class Calculator {

  public static int add(int a, int b) {
    return a + b;
  } 

  public static double add(double a, double b) {
    return a + b;
  }

}
```
---
### Counter Example
```java
package com.revaturelabs;

public class Calculator 
{

  public static int add(int a, int b) 
  {
    return a + b;
  } 

  public static double add(double a, double b) 
  {
    return a + b;
  }

}
```
