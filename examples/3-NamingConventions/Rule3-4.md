# Rule 3.4 - When applicable, Generic Type parameters should be a single, uppercase letter.
### Example
```java
package com.revaturelabs;

import java.util.Collection;

public interface Container<T> {
  
  Collection<T> getItems();
}
```
```java
package com.revaturelabs;

import java.util.Collection;

public class IntegerContainer implements Container<Integer> {

  @Override
  public Collection<Integer> getItems() {
    return null;
  }
}
```

--- 
### Counter Example
```java
package com.revaturelabs;

import java.util.Collection;

// Not OK - It'll compile, but terribly confusing
public interface Container2<items> {
  
  Collection<items> getItems();
}
```
```java
package com.revaturelabs;

import java.util.Collection;

public class IntegerContainer2 implements Container2<Integer> {

  @Override
  public Collection<Integer> getItems() {
    return null;
  }
}
```
