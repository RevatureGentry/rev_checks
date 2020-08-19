# Rule 3.2 - Methods, Method Arguments, non-constant variables follow _camelCase_, also known as _lowerCamelCase_
### Example 
```java
package com.revaturelabs;

import java.util.Map;
import java.util.LinkedHashMap;

public class AddressBook {

  // OK - although myContacts is marked as final, the REFERENCE can't be reassigned but you can still change the contents of the map
  private final Map<String, PhoneNumber> myContacts = new LinkedHashMap<>();

  // OK - variable follows camelCase
  private String username;

  // ...

  // Method Name, Method Argument - OK
  public void addContact(Contact toBeAdded) {
    myContacts.put(toBeAded.getName(), toBeAdded.getPhoneNumber());
  }

  // Method Name, Method Argument - OK
  public void removeContact(String nameOfContactToBeRemoved) {
    myContacts.remove(nameOfContactToBeRemoved);
  }
}
```
---

### Counter Example 
```java
package com.revaturelabs;

import java.util.Map;
import java.util.LinkedHashMap;

public class AddressBook {

  // Not OK - although the reference cannot be reassigned, the contents of the map can change
  private final Map<String, PhoneNumber> MY_CONTACTS = new LinkedHashMap<>();

  // Not OK - variable follows snake case
  private String user_name;

  // ...

  // Method Name, Not OK - PascalCase
  // Method Argument, Not OK - mix of camel case and snake case
  public void AddContact(Contact to_Be_Added) {
    MY_CONTACTS.put(to_Be_Added.getName(), to_Be_Added.getPhoneNumber());
  }

  // Method Name, Not OK - snake case
  // Method Argument, Not OK - Pascal case
  public void remove_contact(String NameOfContactToBeRemoved) {
    MY_CONTACTS.remove(NameOfContactToBeRemoved);
  }
}
```
