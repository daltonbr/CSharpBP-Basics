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