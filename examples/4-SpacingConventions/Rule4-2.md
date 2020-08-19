# Rule 4.2 - Horizontal Spacing
## Rule 4.2.1 - One single space will occur after each of the following, where there is an opening parenthesis that follows it on that line
* `if`
* `for`
* `while`
* `try`
* `do`
* `catch`

## Rule 4.2.2 - One single whitespace will occur before and after the following
* The `?` and `:` in a ternary operator
* The `:` in an enhanced for-loop
* The `|` in a multi-catch block
* The assignment operator `=`
* Any binary operation 

### Example
```
if (true) {
  // ...
}

for (int i = 0; i < 10; i++) {
  // ...
}

for (Foo foo : foos {
  // ...
}

while (true) {
  // ...
}

do {
  // ...
} while (true);

try {
  // ...
} catch (IOException | RuntimeException e) {
  // ...
}

x += 1;

String normalizedName = getName() == null ? "default" : getName().toLowerCase();
```
--- 
### Counter Example
```
// Not OK
if(true){
  // ...
}

// Not OK
for(int i = 0; i < 10; i++){
  // ...
}

// Not OK
while(true){
  // ...
}

// Not OK
do{
  // ...
}while (true);

// Not OK
try{
  // ...
}catch (IOException|RuntimeException e){
  // ...
}

x+=1;

String normalizedName=getName()==null?"default":getName().toLowerCase();
```
