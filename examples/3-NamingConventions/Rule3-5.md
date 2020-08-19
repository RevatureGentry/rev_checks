# Rule 3.5 - Under no circumstances should a reference name be abbreviated or in shorthand.
### Example
```java
package com.revaturelabs;

@Service
public class TodoService {

  // OK - we know clearly what we are referring to, even on a method on line 250
  @Autowired
  private TodoRepository todoRepository;

}
```

---

### Counter Example
```java
package com.revaturelabs;

@Service
public class TodoService {

  // Not OK - we see `tr.getById` in a method on line 250, and we'll have to scroll up to the declaration
  @Autowired
  private TodoRepository tr;

}
```
