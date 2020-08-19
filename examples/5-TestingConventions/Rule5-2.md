# Rule 5.2 - Unit Tests should never be written for IDE generated code
  * **Exception**: Test your getters, setters, or constructors IF they employ some custom logic
### Example
```java
package com.revaturelabs;

public class Todo {

  private long id;
  private String name;

  public Todo() {}
    
  public Todo(long id, String name) {
      this.id = id;
      this.name = name;
  }

  public long getId() {
      return id;
  }

  public void setId(long id) {
      this.id = id;
  }

  public String getName() {
      return name;
  }

  public void setName(String name) {
      this.name = name;
  }

  @Override
  public boolean equals(Object o) {
      if (this == o) return true;
      if (o == null || getClass() != o.getClass()) return false;
      Todo todo = (Todo) o;
      return getId() == todo.getId() &&
                      Objects.equals(getName(), todo.getName());
  }

  @Override
  public int hashCode() {
      return Objects.hash(getId(), getName());
  }

  @Override
  public String toString() {
    final StringBuilder sb = new StringBuilder("Todo{");
    sb.append("id=").append(id);
    sb.append(", name='").append(name).append('\'');
    sb.append('}');
    return sb.toString();
  }
}
```
```java
package com.revaturelabs;

import static org.assertj.core.api.Assertions.assertThat;

public class TodoTest {
  
  private Todo todo;
 
  @BeforeEach
  void setUpTodo() {
    todo = new Todo(1, "Todo");
  }

  @Test
  void shouldReturnId() {
    assertThat(todo.getId()).isOne();
  }

  @Test
  void shouldReturnName() {
    assertThat(todo.getName()).isEqualTo("Todo");
  }

}
```
