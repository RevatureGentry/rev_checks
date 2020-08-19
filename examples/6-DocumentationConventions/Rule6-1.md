# Rule 6.1 - Javadocs are intended for users of your code, Multi-Line Comments are for future developers

### Example
```java
package com.revature;

/**
 * Utility Class to handle the serialization and deserialization from many sources into a @link{com.revaturelabs.Todo}
 */
public class TodoUtil {

  /*
   *  This implementation needs optimization
   */
  public static Todo fromFile(File file) {
    // ...
    return todoFromFile;
  }

}
```
---
### Counter Example
```java
package com.revature;

/**
 * Current implementation needs optimization
 */
public class TodoUtil {
  
  public static Todo fromFile(File file) {
    // ...
    return todoFromFile;
  }

}
```
