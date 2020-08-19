# Rule 1.3: Structure of Class Members
1. Static Fields
2. Instance Fields
3. Static Initializers
4. Instance Initializers
5. Constructors
6. Inherited Method Implementations
7. Getters/Setters 
8. `hashCode` and `equals` implemented
9. `toString` implemented***
10. Helper Methods (if applicable)
11. Nested Members (if applicable)
* **Note**: Overloaded methods should be directly after the original method
* **Note**: `toString` is difficult to enforce programmatically without getting in the way - you wouldn't want to implement `toString` for `com.revature.service.TodosService`, but you'd want to for `com.revature.model.Todo`

### Example
```java
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

package com.revature.geometry;

import static java.lang.Math.PI;
import static java.lang.Math.pow;

public class Circle {

  // 1. Static Field - OK
  private static final int UNIT_CIRCLE_RADIUS = 1;
	
  // 2. Instance Field - OK
  private final int radius;

  // 3. No Static Initializers - OK

  // 4. No Instance Initializers - OK

  // 5. Constructor - OK
  public Circle(int radius) {
    this.radius = radius;
  }

  // 6. Overloaded Constructor - OK
  private Circle() {
    this(1);
  }

  // 7a. Getter - OK
  public int getRadius() {
    return radius;
  }

  public double getArea() {
    return pow(PI * radius, 2);
  }

  public double getCircumference() {
    return 2 * PI * r;
  }

  public int getDiameter() {
    return 2 * r;
  }

  // 7b. No Setters - OK, com.revature.geometry.Circle is immutable => no setters

  // 8. hashCode and equals implemented
  @Override
  public boolean equals(Object o) {
  	if (this == o) return true;
  	if (o == null || getClass() != o.getClass()) return false;
  	Circle circle = (Circle) o;
  	return radius == circle.radius;
  }
  
  @Override
  public int hashCode() {
  	return Objects.hash(radius);
  }

  // 9. Helper Method - OK
  public static Circle getUnitCircle() {
    return new Circle();
  }
  
}
```
---

### Counter Example
```java
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

package com.revature.ecommerce;

// Wildcard imports - sneaky, but still not OK
import java.util.*;

public class Cart {

  // Instance Variable - OK
  private Set<Product> products = new HashSet<>();

  // Static Method - Not OK, should be after toString
  public static Cart newInstance() {
    return new Cart();
  }

  // Intsance Method - Not OK, should be after toString
  public void addItemToCart(String name, double amount) {
    this.products.add(new Product(name, amount));
  }

  // Constructor - Not OK, should be directly after Instance Variable (or Initializers, when applicable)
  private Cart() {}

  // Nested Member - Not OK, should be at end of class
  public static class Product {
    private String name;
    private double amount;

    // Getters/Setters - Not OK, not grouped together
    public String getName() {
      return name;
    }

    public void setName(String name) {
      this.name = name;
    }

    // Constructor - Not OK, should be after instance fields
    public Product(String name, double amount) {
      this.name = name;
      this.amount = amount;
    }

    public double getAmount() {
      return amount;
    }

    // hashCode/equals implemented, OK, but... hashCode not implemented correctly. Not OK
    @Override
    public boolean equals(Object o) {
      if (this == o) return true;
      if (o == null || getClass() != o.getClass()) return false;
      Product product = (Product) o;
      return Double.compare(product.getAmount(), getAmount()) == 0 &&
              Objects.equals(getName(), product.getName());
    }

    @Override
    public int hashCode() {
      return 1;
    }

    @Override
    public String toString() {
      final StringBuilder sb = new StringBuilder("Product{");
      sb.append("name='").append(name).append('\'');
      sb.append(", amount=").append(amount);
      sb.append('}');
      return sb.toString();
    }

    public void setAmount(double amount) {
      this.amount = amount;
    }
  }

  // Instance Method - OK
  public double total() {
    return products.stream().mapToDouble(Product::getAmount).sum();
  }
}

```
