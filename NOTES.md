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

## Singleton

##Static Class