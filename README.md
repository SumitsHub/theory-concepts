# Theory concepts related to Software Development

## Topics Index
01. Coding Principles




### 01. Coding Principles
Most commonly used coding principles:

1. DRY (Don't Repeat Yourself)
- Principle: Avoid duplicating code. If the same piece of logic is repeated in multiple places, it should be abstracted into a single, reusable function or module.

- Example:
```js
// Bad: Repeated logic
function calculateArea(length, width) {
    return length * width;
}

function calculateVolume(length, width, height) {
    return length * width * height;
}

// Good: Reusable function
function calculateAreaOrVolume(length, width, height = 1) {
    return length * width * height;
}

```

2. KISS (Keep It Simple, Stupid)
- Principle: Code should be as simple as possible. Avoid unnecessary complexity, as simple code is easier to read, maintain, and debug.

- Example:
```py
# Bad: Overly complex
def is_even(number):
    return number % 2 == 0

# Good: Simpler and more understandable
def is_even(number):
    return not number % 2

```

3. YAGNI (You Aren't Gonna Need It)
- Principle: Only implement what is necessary. Avoid adding functionality until it is needed, as doing so can lead to unnecessary complexity.

- Example:
```js
// Bad: Adding unnecessary methods in advance
class User {
    String name;
    String email;

    void sendEmail(String message) {
        // Implementation
    }

    void scheduleEmail(String message, Date date) {
        // Not needed yet, avoid implementing
    }
}

// Good: Only implement what is necessary
class User {
    String name;
    String email;

    void sendEmail(String message) {
        // Implementation
    }
}

```

4. SOLID Principles
- Principle: A set of five design principles aimed at making software designs more understandable, flexible, and maintainable.
    - Single Responsibility Principle (SRP): A class should have only one reason to change.
    - Open/Closed Principle (OCP): Software entities should be open for extension but closed for modification.
    - Liskov Substitution Principle (LSP): Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
    - Interface Segregation Principle (ISP): No client should be forced to depend on methods it does not use.
    - Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules. Both should depend on abstractions.

- Example:
```js
// Bad: A class with multiple responsibilities
public class User {
    public void GetUserData() { /* ... */ }
    public void SaveToDatabase() { /* ... */ }
    public void SendEmail() { /* ... */ }
}

// Good: Separate classes for each responsibility
public class UserData {
    public void GetUserData() { /* ... */ }
}

public class UserRepository {
    public void SaveToDatabase() { /* ... */ }
}

public class EmailService {
    public void SendEmail() { /* ... */ }
}

```

5. Separation of Concerns
- Principle: Different parts of a program should be responsible for different concerns or functionalities. This leads to better organization, easier maintenance, and more modular code.

- Example:
```html
<!-- Bad: Mixing HTML, CSS, and JavaScript -->
<div style="color: red;" onclick="alert('Clicked!')">Click Me</div>

<!-- Good: Separation of concerns -->
<!-- HTML -->
<div id="clickable">Click Me</div>

<!-- CSS -->
<style>
    #clickable {
        color: red;
    }
</style>

<!-- JavaScript -->
<script>
    document.getElementById('clickable').addEventListener('click', function() {
        alert('Clicked!');
    });
</script>

```

6. Code Reusability
- Principle: Write code in such a way that it can be reused in other parts of the application or even in other projects. This reduces redundancy and improves maintainability.

- Example:
```py
# Bad: Duplicating code
def calculate_circle_area(radius):
    return 3.14 * radius * radius

def calculate_square_area(side):
    return side * side

# Good: Reusing code
def calculate_area(shape, dimension):
    if shape == 'circle':
        return 3.14 * dimension * dimension
    elif shape == 'square':
        return dimension * dimension

```

7. Encapsulation
- Principle: Keep the internal details of a class or module hidden from the outside world, exposing only what is necessary. This promotes modularity and protects the integrity of the data.

- Example:
```ts
// Bad: Exposing internal state
class User {
    public String name;
}

// Good: Encapsulation through private fields and public methods
class User {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

These principles help in writing clean, maintainable, and scalable code. They form the foundation of good software engineering practices.
