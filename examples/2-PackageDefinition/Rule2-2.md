# Rule 2.1: All packages should start with the reverse domain name `com.revature` or `com.revaturelabs`

# Rule 2.2: All Packages should be separated by _feature/domain_, not by _layer_
### Example - Split by Domain
```java
package com.revature.grade;

public class Grade {}
``` 

```java
package com.revature.grade;

public interface GradeDao {}
``` 

```java
package com.revature.grade;

public class GradeDaoImpl implements GradeDao {}
``` 

```java
package com.revature.grade;

public class GradeService {}
```

```java
package com.revature.grade;

public class GradeController {}
```

---

### Counter Example - Split by Layer
```java
package com.revature.model;

public class Grade {}
``` 

```java
package com.revature.data;

public interface GradeDao {}
``` 

```java
package com.revature.data;

public class GradeDaoImpl implements GradeDao {}
``` 

```java
package com.revature.service;

public class GradeService {}
```

```java
package com.revature.web;

public class GradeController {}
```
