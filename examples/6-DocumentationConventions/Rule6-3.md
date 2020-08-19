# Rule 6.3 - Documentation is only required for logic that you write.
* Not necessary if the documentation is for IDE generated code, or from a commonly used library 

### Example
```java
package com.revaturelabs;

import com.revaturelabs.foo.FooForm;

public class FooFinder {

  // Accepts a JSON object in the shape of a com.revaturelabs.foo.FooForm,
  // and finds the Foo that matches the criteria provided
  // The underlying algorithm for this method is a topological sort
  public Foo findBest(FooForm fooForm) {
    // .. Logic that YOU wrote
    return bestFoo;
  }

}
```
---
### Counter Example
```java
package com.revaturelabs;

public class Todo {
  
  private String name;

  // ...

  // Returns the name of the Todo
  public String getName() {
    return name;
  }
  
}
```
