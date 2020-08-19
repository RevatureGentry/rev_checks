# Rule 6.2 - Comments appear one line directly above the intended target

### Example
```java
package com.revature;

public class FooCalculator {

  // Calculates the arithmetic average foo
  public double average(Foo ...foos) {
    // ...
    return fooAverage;
  }
}
```
---
### Counter Example
```java
package com.revature;

public class FooCalculator {
  
  public double average(Foo ...foos) { // Calculates the arithmetic average foo
    // ...
    return fooAverage;
  }
}
```
