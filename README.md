# Theory concepts related to Software Development

## Topics Index
01. Coding Principles
02. SonarLint & SonarQube 
03. Semantic Versioning
04. Tree Shaking
05. ESLint and Linting
06. React Design Patterns
07. NodeJS Design Patterns
08. Reactor Pattern



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


### 02. SonarLint & SonarQube

#### SonarLint
SonarLint is a static code analysis tool that helps developers identify and fix issues in their code as they write it. It integrates with popular IDEs (like Visual Studio Code, IntelliJ IDEA, and Eclipse) and provides real-time feedback on code quality.

- How it works: As you write code, SonarLint analyzes it in the background and highlights potential issues, such as bugs, security vulnerabilities, and code smells (more on code smells below). It suggests fixes and best practices, enabling you to maintain code quality from the beginning.

- Example: Suppose you're writing Java code in IntelliJ IDEA. If you introduce a potential null pointer exception or a piece of code that is overly complex, SonarLint will underline the problematic code and provide suggestions to resolve the issue.

#### SonarQube
SonarQube is a more comprehensive tool that provides static code analysis on a larger scale, typically integrated into a continuous integration/continuous deployment (CI/CD) pipeline.

- How it works: SonarQube analyzes code in your repository for bugs, vulnerabilities, code smells, and other quality issues. It generates detailed reports, visualizes metrics, and tracks code quality over time.

- Usage in CI/CD: SonarQube is often used in automated build processes to ensure that code meets quality standards before it is deployed. If the code doesn't pass the quality gates (a set of predefined quality criteria), the build can fail, preventing bad code from reaching production.

- Integration: SonarQube can be integrated with various version control systems (like Git) and CI/CD tools (like Jenkins, GitLab CI, etc.). It supports multiple programming languages and can be customized to fit the needs of different projects.


##### Code Smell
Code smell refers to any symptom in the code that indicates a deeper problem. While a code smell doesn't necessarily cause bugs or crashes, it suggests that the code might be poorly designed, difficult to maintain, or prone to future issues.

- Examples of code smells:
    - Duplicated Code: Similar or identical code appearing in multiple places, which violates the DRY principle.
    - Long Methods: Methods that are too long and do too much, making them hard to understand and maintain.
    - Large Classes: Classes that have too many responsibilities, violating the Single Responsibility Principle (SRP).
    - Magic Numbers: Using hardcoded numbers without explanation, making the code less readable and harder to maintain.
    - Comments: Over-reliance on comments can indicate that the code is not self-explanatory or well-structured.

#### How SonarLint and SonarQube Help with Code Smells
- SonarLint: Detects code smells in real-time as you write code and suggests refactoring options to improve code quality.
- SonarQube: Provides a more extensive analysis of code smells across an entire codebase. It highlights areas that may need refactoring and tracks the improvement of code quality over time.


#### Related Concepts
- Static Code Analysis: The process of examining code without executing it, to find potential issues like bugs, security vulnerabilities, and code smells.
- Technical Debt: Refers to the extra work that arises when code quality is sacrificed in the short term for quick fixes or faster delivery. Code smells often contribute to technical debt.
- Quality Gates: A set of criteria used by SonarQube to determine whether a piece of code meets the required quality standards. If code doesn't pass these gates, it can be flagged for review or rejected from being merged/deployed.


SonarLint and SonarQube are powerful tools in maintaining and improving code quality by providing real-time feedback and comprehensive analysis. They help developers adhere to best practices, reduce technical debt, and ensure that code remains clean, maintainable, and secure.




### 03. Semantic Versioning
Semantic Versioning (often abbreviated as SemVer) is a versioning system used widely in the software development world, including for Node.js packages, to manage and communicate changes in a consistent and understandable way.
It provides a structured approach to versioning that helps developers understand the impact of changes in a software package.

#### The Semantic Versioning Format
A version number under SemVer is represented as:
```bash
MAJOR.MINOR.PATCH
```

Each part of this version number has a specific meaning:

1. MAJOR: Indicates incompatible API changes. Incrementing this number signifies that the changes made to the package are not backward-compatible. Users of the package may need to modify their code to accommodate these changes.

2. MINOR: Indicates the addition of new functionality in a backward-compatible manner. When this number is incremented, it means new features have been added, but the existing functionality remains unchanged and still works as before.

3. PATCH: Indicates backward-compatible bug fixes. Incrementing this number means that bugs have been fixed without introducing any new features or breaking existing functionality.

#### Example of Semantic Versioning
Given a version number 2.5.3:

2 is the MAJOR version.
5 is the MINOR version.
3 is the PATCH version.

#### Pre-release Versions and Build Metadata
Semantic Versioning also allows for pre-release versions and build metadata:

Pre-release Versions: Indicated by appending a hyphen and a series of dot-separated identifiers. For example, 1.0.0-alpha, 1.0.0-beta.2. These versions are used to signal that the release is unstable and might not meet the final version's quality requirements.

Build Metadata: Indicated by a plus sign and a series of dot-separated identifiers. For example, 1.0.0+001. Build metadata is ignored when determining version precedence, but it can provide additional information.

#### Versioning and Compatibility
Backward Compatibility: Semantic Versioning helps maintain backward compatibility by communicating the type of changes through the version number. Consumers of the package can understand if a new version will work with their current setup.

Caret (^) and Tilde (~) Ranges: In package.json, caret (^) and tilde (~) are used to specify compatible version ranges for dependencies:

Caret (^): Allows updates that do not change the leftmost non-zero digit. For example, ^1.2.3 allows versions >=1.2.3 and <2.0.0.

Tilde (~): Allows updates to the patch version, but not the minor version. For example, ~1.2.3 allows versions >=1.2.3 and <1.3.0.

#### Benefits of Semantic Versioning
Predictability: It clearly indicates the impact of a new version. Developers can expect backward compatibility for MINOR and PATCH changes, and understand that MAJOR changes might require modifications.

Dependency Management: Package managers (like npm) can automatically handle dependency updates based on versioning constraints defined in package.json, making it easier to keep packages up to date while avoiding breaking changes.

Communication: It provides a common language for communicating about changes, making it easier for developers to collaborate and for users to understand the stability and compatibility of a package.


### 04. Tree Shaking
Tree shaking is a technique used in modern software development, particularly in the context of JavaScript and frontend frameworks, to optimize the size of the final output bundle by eliminating unused code. 

The term "tree shaking" comes from the idea of shaking a tree to remove the dead leaves; similarly, tree shaking removes "dead" (unused) code from the final bundle.

#### How Tree Shaking Works
Tree shaking analyzes the code to determine which parts are actually being used and which can be safely removed. It is typically implemented by JavaScript bundlers like Webpack, Rollup, or Parcel, and relies on the ES6 (ECMAScript 2015) module system, which provides static import/export declarations that make it easier to analyze the dependency graph.

Here’s a high-level overview of how tree shaking works:

Static Analysis of Imports/Exports: Tree shaking relies on the ability to statically analyze the imports and exports in your code. The ES6 module system is designed for this, as it allows the bundler to understand exactly what is being imported and exported without executing the code. This static nature enables the bundler to trace which exports are actually used.

Dead Code Elimination: Once the bundler knows which parts of the code are not used (dead code), it can remove those parts from the final bundle. Dead code elimination is the process of removing code that is never called or used.

Minification: After tree shaking, the remaining code is usually minified, which means it's further compressed to reduce file size by removing unnecessary characters, spaces, and comments. This step is separate but often goes hand-in-hand with tree shaking.

#### Example of Tree Shaking
Consider a simple example:

```javascript
Copy code
// utils.js
export function add(a, b) {
    return a + b;
}

export function multiply(a, b) {
    return a * b;
}

// main.js
import { add } from './utils';

console.log(add(2, 3));

```

In this example:

- The utils.js file exports two functions: add and multiply.
- The main.js file only imports and uses the add function.

* Without Tree Shaking: Both add and multiply functions would be included in the final bundle, even though multiply is never used.

* With Tree Shaking: The bundler analyzes the code, sees that multiply is never used, and removes it from the final bundle. This results in a smaller and more efficient bundle.


#### Prerequisites for Effective Tree Shaking
For tree shaking to work effectively, certain conditions should be met:

- ES6 Modules: Your codebase should use ES6 import/export syntax (import and export). CommonJS modules (require and module.exports) don't support tree shaking because their imports and exports are dynamic and not statically analyzable.

- Bundler Support: You need a bundler that supports tree shaking, such as Webpack, Rollup, or Parcel. These tools can detect unused exports and exclude them from the final bundle.

- Configuration: Proper configuration is required in the bundler to enable tree shaking. For example, in Webpack, you might need to set the mode to production, use the optimization settings, and ensure that the package’s sideEffects flag is correctly set in package.json.


#### Benefits of Tree Shaking
- Reduced Bundle Size: By removing unused code, tree shaking helps to reduce the size of the JavaScript bundle. This is especially beneficial for large applications with many dependencies, as it ensures that only the code that is actually used gets shipped to the client.

- Improved Performance: Smaller bundle sizes mean faster load times, which can improve the performance of web applications. This is crucial for user experience, especially on mobile devices or slower networks.

- Reduced Memory Usage: Less code means less memory usage, which can improve the performance of the application, especially in resource-constrained environments.

- Better Maintainability: Developers can focus on writing modular code, knowing that unused modules won't bloat the final build, making it easier to manage and refactor.


#### Conclusion
Tree shaking is a powerful optimization technique that is essential for modern JavaScript development, especially for large-scale applications. By eliminating unused code, it helps developers create faster, leaner, and more efficient applications. Using tree shaking requires writing modular code, choosing libraries that support it, and configuring the build process correctly. As the JavaScript ecosystem continues to evolve, tree shaking remains a key practice for performance optimization.


### 05. ESLint and Linting

#### What is Linting?
Linting is the process of running a program (linter) to analyze code for:
- Syntax errors.
- Coding style issues (e.g., indentation, spacing).
- Bugs or potential runtime issues.
- Best practice violations.

Linting improves readability, maintainability, and helps in catching bugs early.

#### What is ESLint?
ESLint is a popular open-source tool for linting JavaScript and modern JavaScript frameworks like React, Angular, or Vue. It analyzes your code to identify potential errors, stylistic issues, and best practice violations, helping maintain consistent and clean code.

#### Why Use ESLint?
1. Consistent Codebase: Ensures all developers follow the same coding standards.
2. Avoid Common Errors: Catches errors like unused variables, mismatched imports, or undefined variables.
3. Integration with Editors: Works with tools like VSCode for real-time linting.
4. Extensibility: Supports plugins for frameworks (e.g., eslint-plugin-react, eslint-plugin-vue).

#### Steps to Integrate ESLint in a Project
1. Install ESLint
```bash
npm install eslint --save-dev
```

2. Initialize ESLint Generate a configuration file (.eslintrc) by running:
```bash
npx eslint --init
```
During setup, you’ll be asked:
- What framework you're using (React, Vue, etc.).
- Which style guide to follow (Airbnb, Standard, or custom).
- Whether to use JavaScript, JSON, or YAML for configuration.

3. Install Additional Plugins For example, in a React project:

```bash
npm install eslint-plugin-react eslint-plugin-react-hooks --save-dev
```
4. Configure .eslintrc Example configuration for React

```json
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "airbnb"
  ],
  "parserOptions": {
    "ecmaVersion": 12,
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "plugins": ["react", "react-hooks"],
  "rules": {
    "react/prop-types": "off",
    "no-unused-vars": "warn",
    "react/jsx-props-no-spreading": "off"
  }
}

```

5. Run ESLint
- Check specific files:
```bash
npx eslint src/**/*.js
```
- Fix issues automatically:
```bash
npx eslint src/**/*.js --fix
```

6. Integrate ESLint with VSCode
- Install the ESLint extension from the VSCode marketplace.
- Enable eslint.autoFixOnSave in your VSCode settings.

#### How the Linting Process Works
1. ESLint Scans Files: Matches your code against defined rules.
2. Generates a Report: Lists problems with file name, line number, and issue type.
3. Fix Issues:
   - Manually: Correct issues based on the report.
   - Automatically: Run ESLint with --fix for auto-fixable problems.


#### Commonly Used ESLint Rules
1. Code Quality:
    "eqeqeq": "error" → Enforces strict equality checks (=== vs ==).
    "no-console": "warn" → Warns about console.log statements.
2. Stylistic Issues:
    "semi": ["error", "always"] → Requires semicolons.
    "quotes": ["error", "single"] → Enforces single quotes.
3. Best Practices:
    "react-hooks/rules-of-hooks": "error" → Validates React Hooks usage.
    "react/jsx-uses-react": "off" → For React 17+, avoids importing React.

#### Benefits of Using ESLint
Prevents Bugs: Catch potential issues early in the development process.
Improves Readability: Enforces consistent formatting and style.
Saves Time: Reduces code review time by automating style checks.
Encourages Best Practices: Guides developers to write better code.


### 06. React Design Patterns
React applications often use design patterns to create scalable, maintainable, and reusable code.

1. Container-Presenter Pattern
Purpose: Separates logic (state management) from UI rendering.
Structure:
- Container Components: Handle business logic, state, and data fetching.
- Presenter Components: Pure components responsible for rendering UI.
Benefits:
- Clear separation of concerns.
- Easier to test and maintain.

```js
// Container Component
const TodoContainer = () => {
  const [todos, setTodos] = useState([]);

  useEffect(() => {
    fetch('/api/todos')
      .then(res => res.json())
      .then(data => setTodos(data));
  }, []);

  return <TodoList todos={todos} />;
};

// Presenter Component
const TodoList = ({ todos }) => (
  <ul>
    {todos.map(todo => (
      <li key={todo.id}>{todo.title}</li>
    ))}
  </ul>
);

```

2. Higher-Order Component (HOC) Pattern
Purpose: Reuses component logic by wrapping a component.
Structure: A function takes a component as input and returns a new component with added functionality.
Benefits: Promotes code reuse.

```js
const withLogging = (WrappedComponent) => {
  return (props) => {
    useEffect(() => {
      console.log('Component mounted');
      return () => console.log('Component unmounted');
    }, []);

    return <WrappedComponent {...props} />;
  };
};

const Button = (props) => <button {...props}>Click me</button>;
const ButtonWithLogging = withLogging(Button);

```

3. Render Props Pattern
Purpose: Shares logic between components using a prop that is a function.
Structure: A component accepts a render function as a prop and uses it to render UI.
Benefits: Flexible and dynamic composition.

```js
const MouseTracker = ({ render }) => {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  const handleMouseMove = (e) => {
    setPosition({ x: e.clientX, y: e.clientY });
  };

  return <div onMouseMove={handleMouseMove}>{render(position)}</div>;
};

const App = () => (
  <MouseTracker
    render={({ x, y }) => (
      <h1>
        Mouse position: {x}, {y}
      </h1>
    )}
  />
);

```

4. Custom Hooks Pattern
Purpose: Encapsulates reusable logic in a custom hook.
Structure: A custom hook is a JavaScript function that uses React hooks.
Benefits: Clean and reusable logic for state and side effects.

```js
const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then(setData)
      .catch(setError);
  }, [url]);

  return { data, error };
};

const App = () => {
  const { data, error } = useFetch('/api/data');

  if (error) return <div>Error: {error.message}</div>;
  if (!data) return <div>Loading...</div>;

  return <div>{JSON.stringify(data)}</div>;
};

```

5. Compound Components Pattern
Purpose: Allows components to work together as a "compound" while maintaining flexibility.
Structure: Parent component provides context, and child components use it.
Benefits: Clean API for users of the component.

```js
const Tabs = ({ children }) => {
  const [activeIndex, setActiveIndex] = useState(0);

  return React.Children.map(children, (child, index) =>
    React.cloneElement(child, {
      isActive: index === activeIndex,
      onClick: () => setActiveIndex(index),
    })
  );
};

const Tab = ({ isActive, onClick, children }) => (
  <button
    onClick={onClick}
    style={{ fontWeight: isActive ? 'bold' : 'normal' }}
  >
    {children}
  </button>
);

const App = () => (
  <Tabs>
    <Tab>Tab 1</Tab>
    <Tab>Tab 2</Tab>
    <Tab>Tab 3</Tab>
  </Tabs>
);

```

6. Context API Pattern
Purpose: Shares global state without prop drilling.
Structure: A Provider supplies data, and consumers access it via useContext.
Benefits: Avoids passing props through multiple levels.

```js
const ThemeContext = React.createContext();

const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

const ThemeToggler = () => {
  const { theme, setTheme } = useContext(ThemeContext);
  return (
    <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
      Toggle Theme: {theme}
    </button>
  );
};

const App = () => (
  <ThemeProvider>
    <ThemeToggler />
  </ThemeProvider>
);

```

7. State Reducer Pattern
Purpose: Manages complex state transitions in a single location.
Structure: Uses useReducer or custom reducers for predictable state management.
Benefits: Simplifies state logic and transitions.

```js
const reducer = (state, action) => {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
};

const Counter = () => {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <span>{state.count}</span>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
    </div>
  );
};

```



### 07. NodeJS Design Patterns
#### 1. Module Pattern
Purpose: Encapsulates code into reusable modules.
How It Works:
- Leverages require or import to manage dependencies.
- Separates functionality into self-contained modules.
Benefits:
- Encourages separation of concerns.
- Simplifies code management and testing.

```js
// math.js (Module)
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
module.exports = { add, subtract };

// app.js
const math = require('./math');
console.log(math.add(2, 3)); // 5

```

#### 2. Singleton Pattern
Purpose: Ensures a class or module has only one instance globally.
How It Works: Exports a single instance of a class or object.
Benefits: Useful for shared resources like database connections or configurations.

```js
// logger.js
class Logger {
  constructor() {
    if (!Logger.instance) {
      Logger.instance = this;
    }
    return Logger.instance;
  }
  log(message) {
    console.log(`[LOG]: ${message}`);
  }
}
module.exports = new Logger();

// app.js
const logger = require('./logger');
logger.log('Application started');

```

#### 3. Factory Pattern
Purpose: Creates objects without specifying the exact class or constructor.
How It Works: Provides a method to instantiate objects based on input.
Benefits: Useful for creating objects dynamically based on runtime conditions.

```js
// carFactory.js
class Sedan {
  drive() {
    console.log('Driving a sedan');
  }
}
class SUV {
  drive() {
    console.log('Driving an SUV');
  }
}
const carFactory = (type) => {
  if (type === 'sedan') return new Sedan();
  if (type === 'suv') return new SUV();
};
module.exports = carFactory;

// app.js
const carFactory = require('./carFactory');
const car = carFactory('suv');
car.drive(); // Driving an SUV

```

#### 4. Middleware Pattern
Purpose: Chains reusable middleware functions to process requests and responses.
How It Works:
- Used extensively in web frameworks like Express.
- Middleware functions handle tasks like logging, authentication, and request parsing.
Benefits:
Clean separation of concerns for request handling.

```js
const express = require('express');
const app = express();

// Middleware
app.use((req, res, next) => {
  console.log(`Request Method: ${req.method}`);
  next();
});

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(3000, () => console.log('Server running on port 3000'));

```

#### 5. Observer Pattern
Purpose: Allows one-to-many dependency between objects where one object's state change notifies others.
How It Works: Commonly implemented using Node.js' built-in EventEmitter.
Benefits: Useful for real-time applications like chat apps or notifications.

```js
const EventEmitter = require('events');
const emitter = new EventEmitter();

emitter.on('message', (msg) => {
  console.log(`Received message: ${msg}`);
});

emitter.emit('message', 'Hello, Observer!');

```

#### 6. Proxy Pattern
Purpose: Acts as an intermediary to control access to an object.
How It Works: Useful for caching, logging, or access control.
Benefits: Adds additional behavior without altering the original object.

```js
const fetchData = () => {
  console.log('Fetching data...');
  return { data: 'Sample Data' };
};

const proxy = (function () {
  let cache = null;
  return {
    getData: () => {
      if (!cache) {
        cache = fetchData();
      }
      return cache;
    },
  };
})();

console.log(proxy.getData());
console.log(proxy.getData()); // Cached data

```

#### 7. Builder Pattern
Purpose: Constructs complex objects step by step.
How It Works: Separates object construction from its representation.
Benefits: Useful for creating objects with multiple optional properties.

```js
class User {
  constructor(name, age, email) {
    this.name = name;
    this.age = age;
    this.email = email;
  }
}

class UserBuilder {
  constructor(name) {
    this.user = new User(name);
  }
  setAge(age) {
    this.user.age = age;
    return this;
  }
  setEmail(email) {
    this.user.email = email;
    return this;
  }
  build() {
    return this.user;
  }
}

const user = new UserBuilder('John')
  .setAge(30)
  .setEmail('john@example.com')
  .build();

console.log(user);

```

#### 8. Strategy Pattern
Purpose: Encapsulates different algorithms or strategies and makes them interchangeable.
How It Works: Delegates behavior to different strategy objects at runtime.
Benefits: Reduces conditional logic and promotes flexibility.

```js
class PayPal {
  pay(amount) {
    console.log(`Paid ${amount} using PayPal`);
  }
}
class CreditCard {
  pay(amount) {
    console.log(`Paid ${amount} using Credit Card`);
  }
}

class PaymentContext {
  constructor(strategy) {
    this.strategy = strategy;
  }
  execute(amount) {
    this.strategy.pay(amount);
  }
}

const payment = new PaymentContext(new PayPal());
payment.execute(100);

```

#### 9. Async Pattern (Callback, Promises, and Async/Await)
Purpose: Handles asynchronous operations efficiently.
How It Works: Leverages patterns like callbacks, Promises, or async/await for non-blocking operations.
Benefits: Avoids callback hell and manages complex async workflows.

```js
const fetchData = async () => {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

fetchData();

```


### 08.Reactor Pattern
#### What is the Reactor Pattern?
The Reactor Pattern is a design pattern commonly used in 'asynchronous' and 'event-driven' programming to handle I/O operations efficiently. It allows a single thread to manage multiple I/O streams, enabling high concurrency and scalability. This is particularly suitable for servers and applications requiring non-blocking I/O, such as Node.js.

##### Key Concepts of the Reactor Pattern
1. Event Loop:
The core of the Reactor Pattern.
Continuously listens for events and dispatches them to appropriate handlers.

2. De-multiplexer:
Monitors multiple file descriptors (I/O resources like sockets or files).
Detects when an I/O operation is ready and notifies the event loop.

3. Event Handlers:
Functions or callbacks that are triggered to handle specific events.

4. Non-Blocking I/O:
Avoids waiting for I/O operations to complete. Instead, the program moves on to handle other tasks.

##### How the Reactor Pattern Works
- The event loop listens for events (e.g., incoming network requests, file read/write readiness).
- When an event occurs, the de-multiplexer notifies the event loop.
- The event loop dispatches the event to the appropriate event handler.
- The event handler processes the event (e.g., reads a file, writes to a socket) and returns control to the event loop.

#### Reactor Pattern in Node.js
Node.js is a prime example of the Reactor Pattern in action. The libuv library, which powers Node.js, implements the Reactor Pattern for handling asynchronous operations.

Node.js Event Loop
1. The event loop is at the heart of Node.js.
2. Handles tasks such as:
    - I/O operations (file system, network requests).
    - Timers (e.g., setTimeout, setInterval).
    - Process events.
3. Runs in a single thread but can manage thousands of concurrent connections due to its non-blocking nature.

