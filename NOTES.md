# C# Best Practices: Improving on the Basics
a PluralSight.com course
by Deborah Kurata
these are Dalton's notes

exercise files:
https://github.com/DeborahK/CSharpBP-Basics

## Types of classes:
* UI classes
* Domain Entity classes
* Library classes

(keyword: MVVM - Model View View Model)

### FAQ:
* Why is a layered architecture important?
    - Logical components are easier to create, change, extend, and maintain
    - Code is easier to reuse

* What is a class
    - A template for the objects created at runtime
    - Specifies the data and operations for each entity

* What are the benefits of unit testing?
    - Higher quality code, faster and easier debugging, and they are repeatable over the life of the application, which helps us to protect the code from multiple developers.

## Building Good (C#) Classes
Classes are made of:
* Signature
* Field
* Properties
* Methods
* Constructors

...and have:
* Accessibility modifier (default is: internal)
* Properties are the getter and setter functions
* Methods are the functions of a class
 
### Class Best Practices:
**DO**: 
* Class naming: Define a meaningful name
* use a noun
* usePascalCasing (aka HighCamelCasing)
* Add XML documentation
* Use properties to encapsulate fields
* Use methods for logic
* Ensure the class has a well-defined purpose
* Create one class per code file
* Add properties above the methods

**AVOID**:
* abbreviations
* prefixes
* underscores
* large classes

### Namespaces
Used to:
* Provide a unique address
* Organize classes into a logical hierarchy
  
#### Namespace Best Practices
**DO**:
* <company>.<technology>.<feature>
    Acme.Wpf.Pm
    Microsoft.Office.Interop.PowerPoint
* Use PascalCasing

**AVOID**:
* Using "System"
* Using a class name (confusing)

### Static Class
* Only static members
* Can not instantiate a static class
* Provides a container for **utility** features
* Can't implement interface, can't inherit from a static class

**DO**:
* Use sparingly
* use for common code library components when needed
**AVOID**:
* Using as a miscellaneous bucket of ad-hoc methods (Every class should have a purpose)

### Singleton (pattern)
 * Provides *only one instance*.
 * *private* constructor(s)
 * Static property provides the one instance
 * Instance accessed with User.Instance

 #### Singletons vs Static Class (advantages)
 * A singleton has an **instance**
 * A singleton can have **child objects**
 * support OOP features
    - can implement an interface
    - can be inherited

### FAQ
* What is the difference between a property and a method?
- Properties are the gate-keepers, providing access to data
- Methods are the operations

* What is a constructor?
- A method executed when a instance is created from a class

* What is the purpose of a **namespace**?
- Organize classes into a logical hierarchy
- Prevent class name collisions

* What is a static class?
- A class that cannot be instantiated
- It's best for use with common code libraries

* What is a singleton?
- A class that provides a single instance of itself (a famous design pattern)

* What is the difference between a static class and a singleton?
- A static class cannot be instantiate
  A singleton can instantiate itself and provide that instance 

  ## Accessing and Using Classes

  To use class from another namespace we must add that class to the recipient's references
  and we have two following options:

* use a fully qualified class name: e.g. Acme.Common.EmailService()
* add a 'using directive to the projet: e.g. using Acme.Common;

* References must be one way
* Avoid use of the 'using static' directive

### Object Initialization

* Setting properties
    When populating from database values
    When modifying properties

* Parameterized constructor
    When setting the basic set of properties

* Object initializers
    When readability is important
    When initializing a subset or superset of properties

### Lazy Loading
    We wait to load or instantiate a related object until it is actually needed

### Null Checking
    **Classic**
    if (currentProduct != null && currentProduct.ProductVendor != null) {
        var companyName = currentProduct.ProductVendor.CompanyName;
    }

    **Null Conditional Operators** C#6 (VisualStudio 2015+)
    
    var companyName = currentProduct?.ProductVendor?.CompanyName;
    
    * '?.' Is the null-conditional operator
    * Called the "Elvis operator"
    * If the variable on the left side is null, then we continue with the dot
    * If the variable on the left side is not null, then we continue with the dot
    * "If null then null; if not the dot" - Mads Torgersen, C# Language PM

### FAQ
* What is the difference between an object and a class?
    - A class is a template that specifies the data and operations for an entity
    - An object is an instance of that class created at runtime using the new keyword

* What is lazy loading and when would you use it?
    - Instantiating related objects when they are needed and not before
    - This often involves creating the instance in the property getter for the related object

## Defining Fields Aprropriately

### Backing Fields
    A variable in a class, holds data for each 
    Data Encapsulation / Information Hiding (Object's data is only accessible to that object)
    Fields are private
    Accessible outside of the class through property getters and setters

### Nullable Types
    - Allows definition of a value OR null
    - Specified with a "?" on the type. e.g. private DateTime? availabilityDate;
    - Distinguishes "not set" from the default value

### Constants
    - A "compile-time" constant
    - const keyword
    - must be a Data type (numbers, boolean or string)
    - Defined in a class
    - Holds a hard-coded value that does not change
    - Must be assigned to an expression that can be fully evaluated at compile time
    - Compiled into every location that references it
    - Are static
    - PascalCasing are more accepted today than all upper case

### Read-Only Fields
    - A "runtime" constant value
    - A variable in a class
    - Holds a value that is initialized and then not changed
    - Must be initialized (in the declaration OR in a constructor)
    - Optional accessibility modifier
    - Optional static keyword
    - readonly keyword
    - Data Type
    - PascalCasing
    - Use static if the constant value is valid for all instances

### FAQ
* Explain the **data encapsulation principle**
    - An object's data should be accessible only to the object
    - Backing fields containing the object data should marked as private

* What is a **backing field**?
    - A variable in a class used to retain each object's data

* When should you use a backing field?
    - For every data field retained for an object

* when should you use a **constant**?
    - When defining a field with a simple data type that will never change

* when should you use a **read-only field**?
    -When defining a field that is initialized from a file, table, or code but should not then be changed anywhere else in the application

* What is the difference between a constant and a read-only field?
    - A constant: is static, assigned on the declaration, assigned to an expression that is fully evaluated at compile time
    - read-only field: can be static or non-static, assigned in the declaration or in a constructor, assigned to any valid expression

## Creating good methods

### Property Accessibility

    **public**: accessible from anywhere
    **protected**: used by the inherited classes
    **internal**: limits access to only the components in which the propery is defined
    **protected**: internal: limits access to the same component and to inherited classes
    **private**: limits access to only the class in which the property is declared

    - the getter **OR** the setter can also have accessibility modifiers, **but not both**

    Rule of thumb:
    Select the **most restrictive** accessibility that still gets the job done

### Expression-Bodied Properties

public string FullName{
    get { return FirstName + " " + Lastname; }
}

public string FullName => FirstName + " " + Lastname;       // C#6 +

* => is called a "fat arrow", but technically it is called a **lambda operator**

### Benefits of properties
    - Fine grained access control
    - Execute code

### FAQ
* What is the primary purpose of a **property**?
    - To guard access to the fields of the class
    - And optionally provide a location for logic

* What are **auto-implemented** properties?
    - Short cut syntax for defining an implict backing field with its associated property getter and setter

* When **should** you use an auto-implemented property?
    - When creating simple properties for a class

* When **shouldn't** you use an auto-implemented property?
    - If the property requires any code in the getter or setter

## Creating Good Methods
* Identify the problem
* Define the single purpose
* Specify the inputs and outputs
* State any assumption
* Consider the errors that could occur

### Building a Method
    - Optional accessibility modifier (Default is private)
    - Return type (void if no return value)
    - Method name (PascalCasing), ofter verbs + noun
    - Parameter list (Empty parenthesis if no parameters)

e.g.: public bool PlaceOrder(Product product, int quantity)

"The first rule of functions is that they should be **small**.
The second rule of functions is that they should be **smaller than that**.
Functions should not be 100 lines long. Functions should hardly ever be 20 lines long."
- Robert Martin
"Clean Code: A handbook of agile software craftsmanship"

**Do:**
- Keep methods short
- Use white space
- Use guard clauses
- Return an expect result (use an object to return multiple values)
- Implement exception handling

**Avoid:**
- void methods (at least we can use a flag)

### XML Document Comment
    * Optional, but it is a good practive to include this
    * Used by to populate intelisense

/// <summary>
/// Sends a product order to the vendor
/// <summary>
/// <param name="product">Product to order.</param>
/// <param name="quantity">Quantity of the product to order.</param>
/// <returns></returns>
public bool PlaceOrder(Product product, int quantity)

### Property or Method
Properties should not change the state of an object, 

### FAQ
* What is the primary purpose of a **method**?
    - To implement the logic required for specific behavior or funcionality in a class

* What is the difference between a parameter and an argument:
    - A **parameter** is part of the method signature
    - An **argument** is part of the method call

* What is the method **overloading**?
    - Methods with the same name and purpose but different signatures

* What is method **chaining**?
    - One method overload calls another overload to prevent repeated code

* When is best to use method overloading vs method overriding?
    - Use **overloding** when one method requires multiple signatures
    - Use **overriding** when replacing a method defined higher up the object hierarchy 

## Specifying clear method parameters
### FAQ
* What is a **named argument** and when should it be used?
    - A named argument uses the parameter name when calling the method
    - Used to clarify the purpose of an argument and define arguments without concern for their position in the parameter list

* How is an **optional parameter** defined?
    - By specifyinga default value

* What is the different between passing an argument by value vs. by reference?
    - When passed **by value** (default), the value of the argument is passed to the method
    - When passed **by reference** (using ref or out), the variable is effectively passed to the method.
    - Because of this, passing by reference enables the method to change the value of the parameter and have that change
    reflected in the calling code

* What is the difference between ref and out?
    - A **ref** parameter requires that the argument be initialized before it is passed
        The method can modify the value for the ref parameter
    - An **out** parameter must be declared, but not initialized before it is passed
        The method **must** provide a value for the out parameter

## Handling Strings
### FAQ
* What does it mean to say that C# strings are **immutable**?
    - It means that strings cannot be modified once they are created

* Is a string a value type or a reference type?
    - A string is a **reference** type
    - That acts like a **value** type

* What is the best way to check for null strings?
    - It depends
    - Using String.IsNullOrWhiteSpace is great when checking nulls for a code block
    - Using the new C#6 null-conditional operator is great for code statements

* What is the benefits of using **StingBuilder**?
    - The .NET StringBuilder class is **mutable**, meaning that it can be readily changed.
    - Using StringBuilder is therefore more efficient when appending lots of strings.

## Final Words
"The ratio of time spent reading (code) versus writing is well over 10 to 1...
(therefore) making it easy to read makes it easier to write."
    
"Clean code always looks like it ws written by someone who cares."
    - Robert Martin "Clean Code"

Clean Code
* Easy to read
* Clear intent
* Simple
* Minimal
* Thoughtful