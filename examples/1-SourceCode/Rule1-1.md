# Rule 1.1: One Top Level Java Class per `.java` File

### Example
```java
// Foo.java - OK
public class Foo {
	
  // Static Nested Class - OK
  public static class Buzz {
  
  } 

  // Nested Class - OK
  public class Bap {

  }
}
```
---
### Counter Example
```java
// Bar.java - Not OK
public class Bar {

}

// Second top level class - Not OK
class Bar2 {
}
```
