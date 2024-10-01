# OOP-Notes-Chapter-8-10

# Chapter 8 Notes

### Viewing and Manipulating Class State
- **Methods**: 
  - Able to view the state of the class (fields).
  - Can manipulate the state (e.g., changing the value of the `passengers` field).

### Constructors
- **Definition**: Constructors are a special type of member in a class.
- **Characteristics**:
  - Executable code that runs **automatically** when an object is created.
  - Used to set the **initial state** of an object.
- **Syntax**:
  - Constructors look like methods but **do not have a return type**.
  - The constructor name is the **same as the class name**.

### Example: Flight Class Constructor
- Adding a constructor to the `Flight` class.
- **Purpose**: Set the initial state of the `Flight` object.
- **Initial State**:
  - `seatsAvailable = 150`
  - `passengers = 0`

## Declaring Math Equation Class

- **Objective**: Start utilizing classes in the `CalcEngine` project.
- **Operating Modes**:
  - Command-line values handled in `handleCommandLine` method.
  - Interactive mode handled in `executeInteractively` method.
  - Array handling now moved to a new method called `performCalculations`.
- **Parallel Arrays**: 
  - Previously used arrays like `leftVals`, `rightVals`, `opCodes`, and `results` were managed with a single index.
  - Using classes allows grouping these values into a single entity, making the code more maintainable.
  
### Creating `MathEquation` Class

1. **Creating the Class**:
   - Navigate to the package, right-click, choose "New" → "Java Class."
   - Name the class `MathEquation`.

2. **Adding Fields to `MathEquation`**:
   - Define fields for `leftVal`, `rightVal`, `opCode`, and `result`.
   - These fields collectively represent the class’s state and will hold data for the mathematical operation.

3. **Adding Methods**:
   - Add an `execute` method to perform the calculations using a switch statement.
   - The `execute` method accesses class fields directly instead of using parameters.

4. **Class State**:
   - Fields like `leftVal`, `rightVal`, and `opCode` hold the input values.
   - The `execute` method performs operations based on these fields.
   - The `result` field stores the outcome of the operation.

## Using Classes

- **Declaring Class Variables**:
  - Declaring a variable of type `Flight` doesn’t create an object. It only creates a reference to a `Flight` object.
  - Use the `new` keyword to create a new `Flight` object (or instance).

- **Memory Allocation**:
  - Using `new` allocates memory and runs the constructor code.
  - The constructor initializes fields like `passengers` and `seats` and returns a reference to the created object.

- **Reference Types**:
  - Java classes are accessed through references, not directly.
  - Multiple variables can point to the same object instance, which means changes made through one reference are reflected in other references.

- **Interacting with Class Members**:
  - Use dot notation (e.g., `flight1.add1Passenger()`) to interact with an object’s methods or fields.

## Creating an Array of Classes

1. **Defining an Array of `MathEquation`**:
   - Declare an array of `MathEquation` type named `equations`.
   - Create a new `MathEquation` array of size 4.
   - Note: This creates an array of references, not instances. Instances must be explicitly created.

2. **Initializing Array Elements**:
   - Use a new method `create` to create and initialize instances of `MathEquation` with the appropriate field values.
   - `create` method sets the fields and returns a new instance of `MathEquation`.

3. **Setting Up the `equations` Array**:
   - Use the `create` method to initialize all elements in the array.
   - Each element in the array references a new `MathEquation` instance with predefined field values.

## Keep In Mind

- **Parallel Arrays vs. Classes**:
  - Using classes to group related data values together is more organized and less error-prone than using parallel arrays.
  - This approach provides better encapsulation and maintainability of code.
  
- **Reference Types Behavior**:
  - Understanding how reference types work is crucial, as it affects how changes to objects are reflected in different parts of the code.

- **Creating and Using Classes**:
  - Create classes to encapsulate data and behavior.
  - Use constructors and methods to define how the class behaves.
  - Use arrays of classes to handle collections of similar objects in a structured manner.

## Using `MathEquation` Class

- **Objective**: Migrate the application to use the `MathEquation` class instead of managing individual arrays.
- **Removal of Arrays**:
  - Remove the code related to handling individual arrays, such as `leftVals`, `rightVals`, `opCodes`, and `results`.
  - Simplify the code by looping through the `MathEquation` array instead.

- **For-Each Loop**:
  - Use a for-each loop to iterate through each element in the `equations` array.
  - Syntax: `for (MathEquation equation : equations)`
  - Each iteration assigns the current `MathEquation` object to the variable `equation`, allowing you to access its methods and fields.

## Encapsulation and Access Modifiers

- **Encapsulation**: The process of bundling data and methods within a class to protect internal state and provide a clear interface.
- **Access Modifiers**:
  - Used to control the visibility and accessibility of class members (fields, methods).
  - Common modifiers include:
    - `private`: Only accessible within the same class.
    - `protected`: Accessible within the same package and by subclasses.
    - `public`: Accessible from any class.

### Benefits of Encapsulation
- Protects internal state from unintended modifications.
- Provides a clear and consistent interface for interacting with the class.
- Makes the code more maintainable and less prone to errors.

### Application of Encapsulation in `MathEquation`
- Fields like `leftVal`, `rightVal`, `opCode`, and `result` are encapsulated within the `MathEquation` class.
- External code interacts with these fields through methods like `execute`, ensuring that changes are made in a controlled manner.

  **Accessor and Mutator Pattern**:
  - Also known as the **getter** and **setter** pattern.
  - **Accessor (Getter)**: Retrieves the value of a field.
    - Named as `getFieldName`.
    - Return type matches the field type.
   
### Benefits of Accessors and Mutators

- Protects the internal state of the class from being altered directly.
- Allows for controlled access and modification of fields.
- Provides flexibility to change the internal representation of fields without affecting external code.

  # Chapter 9 Notes

## Class Initial State

- **Default Field Values**: When a class instance is created, fields are assigned default values:
  - Numeric fields (`int`, `double`, etc.) default to `0`.
  - `char` fields default to a character represented by 0s.
  - `boolean` fields default to `false`.
  - Reference types default to `null`.
- **Custom Initial State**: You can establish custom initial values using:
  1. **Field Initializers**.
  2. **Constructors**.
  3. **Initialization Blocks**.

## Field Initializers

- **Definition**: Set field values as part of the field declaration.
- **Examples**:
  - Simple assignment:  
    ```java
    int circumferenceInMiles = 24901;
    ```
  - Using other fields and calculations:  
    ```java
    long circumferenceInKms = Math.round(circumferenceInMiles * 1.6);
    ```
- **Purpose**: Provides a quick way to set initial values without using additional methods.

## When to Use Field Initializers
- Use for simple assignments and calculations.
- Not suitable when you need to run complex logic—use constructors instead.

## Constructors

- **Definition**: Special methods that run when a class instance is created.
- **Characteristics**:
  - Same name as the class.
  - No return type.
  - Used to initialize class fields and establish a custom initial state.
  - Java provides a default constructor if none is defined.
  
### Multiple Constructors
- Classes can have multiple constructors with unique parameter lists (signatures).
- This allows different ways to create class instances.

### Constructor Overloading
- Each constructor must have a unique parameter list.
- Allows flexibility in how objects are created with different starting states.

## Constructor Chaining

- **Definition**: One constructor calls another within the same class.
- **Syntax**: Use `this(parameterList)` as the first line in the constructor.
- **Benefits**:
  - Avoids code duplication.
  - Centralizes logic for initializing fields.
- **Example**:  
  ```java
  public Passenger(int freeBags, int checkedBags) {
      this(freeBags);  // Calls constructor with one parameter
      this.checkedBags = checkedBags;
  }

## Initialization Blocks

- **Definition**: A block of code that runs automatically when a class instance is created, regardless of which constructor is used.
- **Syntax**: 
  - No parameters.
  - Defined with `{}` outside any method or constructor.

### Key Points
- **Shared Code**: Initialization blocks allow code to be shared across all constructors without needing to duplicate it.
- **Execution Order**: If multiple blocks are defined, they execute in the order they appear in the code.
- **Use Case**: Ideal for setting up common initializations, like setting all elements in an array to a specific value.

### Example: Flight Class
- The `Flight` class uses an initialization block to set all seats in the `isSeatAvailable` array to `true` at the time of object creation.
- This eliminates the need for constructors to handle repetitive initialization logic.

### Initialization Sequence
1. **Field Initializers**: Fields with initial values are set first.
2. **Initialization Blocks**: These run after field initializers.
3. **Constructor**: The code in the constructor runs last.

### Benefits
- Ensures consistency across constructors.
- Avoids the need to chain constructors or duplicate initialization logic.

  # Chapter 9 Notes: Java Textbook

## Constructors
- **Definition**: Special methods that initialize a new object of a class.
- **Characteristics**:
  - Same name as the class.
  - No return type (not even `void`).
  - Automatically called when a new object is created using the `new` keyword.
  
### Purpose of Constructors
- Initialize object fields to desired values.
- Set up initial state of the object.

### Types of Constructors
1. **Default Constructor**:
   - No parameters.
   - Automatically created by the compiler if no constructors are explicitly defined.
2. **Parameterized Constructor**:
   - Accepts arguments to initialize fields with specific values.

### Overloading Constructors
- A class can have multiple constructors with different parameter lists (signatures).
- Allows flexibility in how objects are created.

### Constructor Chaining
- Using `this()` within a constructor to call another constructor in the same class.
- Helps avoid code duplication and centralizes initialization logic.

## Initialization Blocks
- **Definition**: A block of code that runs before the constructor, used to set up initial values.
- Runs before the constructor code executes, regardless of which constructor is called.

## `this` Keyword
- Refers to the current object instance.
- Used for:
  - Differentiating between class fields and method parameters with the same name.
  - Calling another constructor in the same class (`this(parameters)`).

## Garbage Collection
- **Purpose**: Automatically frees up memory by deleting unused objects.
- **How it works**: If no references point to an object, it becomes eligible for garbage collection.
- **Calling `System.gc()`**: Requests garbage collection, but it's not guaranteed to run immediately.

### Finalizers
- **Definition**: A special method (`finalize()`) that gets called when an object is about to be destroyed.
- **Usage**: Rarely used; not recommended for resource management as it can delay cleanup.






