# Rule 1.2: Structure within a `.java` file
1. License (if applicable)
2. Package Declaration
3. Static Import Statements (No wildcards! Be explicit)
4. Import Statements (No wildcards! Be explicit)
5. Top-Level Class Definition

### Example
```java
// 1. Licence - OK
/*
 * Copyright 2020 Revature
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

// 2. Package Declaration - OK
package com.revature.geometry;

// 3. Static imports - OK
import static java.lang.Math.PI;
import static java.lang.Math.pow;

// 4. Imports - OK
import org.apache.logging.log4j.Logger;
import org.apache.logging.log4j.LogManager;

// 5. Top-Level Class - OK
public class Circle {
	
  private final Logger logger = LogManager.getLogger(getClass());
  private final int radius;
  private final double area;
  private final double circumference;
  private final int diameter;

  public Circle(int radius) {
    this.radius = radius;
    this.area = pow(PI * r, 2);
    this.circumference = 2 * PI * r;
    this.diameter = 2 * r;
  }

  public void print() {
    logger.info("Radius: {}, Diameter: {}, Circumference: {}, Area: {}", radius, diameter, circumference, area);
  }

  // getters/setters
  // hashCode/equals
  // toString
}
```
---
### Counter Example

```java
// 2. Package Declaration - Not OK, should come after License
package com.revature.geometry;

// 1. Licence - Not OK, should be first 
/*
 * Copyright 2020 Revature
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

// 4. Imports - Not OK, no wild card, but not grouped with other Import Statement
import org.apache.logging.log4j.Logger;


// 3. Static imports - Not OK, in the correct order, but wildcard
import static java.lang.Math.*;

// 4. Imports - Not OK, no wild card, but not grouped with other Import Statement
import org.apache.logging.log4j.LogManager;

// 5. Top-Level Class - OK
public class Circle {
	
  private final Logger logger = LogManager.getLogger(getClass());
  private final int radius;
  private final double area;
  private final double circumference;
  private final double diameter;

  public Circle(int radius) {
    this.radius = radius;
    this.area = pow(PI * r, 2);
    this.circumference = 2 * PI * r;
    this.diameter = 2 * r;
  }

  public void print() {
    logger.info("Radius: {}, Diameter: {}, Circumference: {}, Area: {}", radius, diameter, circumference, area);
  }

  // getters/setters
  // hashCode/equals
  // toString
```
