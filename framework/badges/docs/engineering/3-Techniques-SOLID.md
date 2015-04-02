# Techniques / SOLID Principles and Design Patterns

Further guidance for the patterns and techniques described in this list can be found in 4-Techniques-SOLID-Explained

| Key         |||
|-----------|:------------:|-----------| 
| Complete understanding of all the concepts and practical knowledge of implementation | W | Working Knowledge 
| Conceptual knowledge of area and may have practical implementation knowledge for one or more concepts | C | Conceptual Knowledge 

### OOP building blocks
| Competency | Bronze | Silver
|-----------|:-------------:|:-------------:
| Abstraction | C | W
| Encapsulation | C | W
| Polymorphism | C | W
| Inheritance | C | W

### Avoiding STUPID Code
| Competency | Bronze | Silver
|-----------|:-------------:|:-------------:
| Singleton | C | W
| Tight Coupling | C | W
| Untestability | C | W
| Indescriptive Naming | C | W
| Duplication | C | W

### SOLID Principles
| Competency | Bronze | Silver
|-----------|:-------------:|:-------------:
| Separation of concerns | C | W
| Open and closed principle | C | W
| Liskov's substitution | C | W
| Interface segregation | C | W
| Dependency inversion principle | C | W

### Code Smells
| Competency | Bronze | Silver
|-----------|:-------------:|:-------------:
| Rigidity | C | W
| Fragility | C | W
| Immobility | C | W
| Viscosity | C | W
| Needless complexity | C | W
| Needless repetition | C | W
| Opacity | C | W

### Design Patterns
| Competency | Bronze | Silver
|-----------|:-------------:|:-------------:
| Mediator |  | C
| Proxy |  | C
| Observer |  | C
| Chain of responsibility |  | C
| Strategy |  | C
| Decorator |  | C
| Factory |  | C
| Singleton |  | C
| Flyweight |  | C
| Adaptor |  | C
| Template Method |  | C
| Builder |  | C
| Iterator |  | C
| Composite |  | C
| State |  | C
| Proxy |  | C
| Command |  | C
| Prototype |  | C
| Command |  | C
| Bridge |  | C
| Interpreter |  | C
| Memento |  | C
| Visitor |  | C
| MVVM |  | C
| MVC |  | C

---- 
## OOP Building Blocks

### Abstraction
http://en.wikipedia.org/wiki/Abstraction
#### Description
Abstraction is concerned with breaking your approach to a problem into natural segments.  The point at which you define the objects that divide the problem into manageable parts.  In terms of object oriented code this is where you are defining your objects properties, public and private and the actions each object needs to perform in the real world.

---- 
### Encapsulation
http://en.wikipedia.org/wiki/Encapsulation_%28object-oriented_programming%29
#### Description
Wrapping methods and data into an object you are encapsulating them, you remove the complexity from view and decide what interface it exposes to the world.
There is an OOP design principle called the Principle of Least Knowledge or sometimes the Law of Demeter sometimes just Effective Encapsulation.  The idea is that for effective OOP you do not want to insist that separate entities know too much about each other.  Where possible the details should be locked away inside each class and make the coupling as loose as possible.

---- 
### Polymorphism
http://en.wikipedia.org/wiki/Polymorphism_%28computer_science%29
#### Description:
Polymorphism (from the Greek many form)  is the provision of a single interface to multiple entities.  It enables you to write code to perform various actions on an object but leaving the decision of what type of object to perform the action on implementation of that object to runtime.  Because multiple objects conform to the same interface they are interchangeable the compiler does not care that the object is of type A or B only that it has the interface Y.

---- 
### Inheritance
http://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming) 
#### Description
Inheritance is the ability of one object to inherit another’s properties and methods.  It is generally used when one class extends another implementing the base classes properties and methods and adding or overriding specific implementation of its own.

---- 
## SOLID

### Separation of concerns
http://en.wikipedia.org/wiki/Separation_of_concerns
Robert C. Martin, Chapter 8, Agile software development principles, patterns and practices, Pearson 2002
#### Description
* A class should only have one reason for change.
* Each responsibility is an an axis for change.  When the requirements change that change will be manifest through a change in responsibility amongst the classes.  If a class assumes more than one responsibility there will be more reason for it to change.
* If a class has more than one responsibility then the responsibilities become coupled.  Changes to one responsibility may impair or inhibit the ability of the class to meet the others = Fragile / Designs that break unexpectedly.
* A responsibility is a reason for change.

---- 
## Open / Closed Principle
http://en.wikipedia.org/wiki/Open/closed_principle
Robert C. Martin, Chapter 9, Agile software development principles, patterns and practices, Pearson 2002
Description
Software entities should be open for extension but closed for modification.

### Open for Extension
As requirements of the application change we are able to extend the module with new behaviours that satisfy those changes.  In other words words, we are able to change what the module does.
### Closed for Modification
Extending the behaviour of a module does not result in changes to the source or binary code of the module.

* No matter how closed a module is there will always be some kind of change against which it is not closed.
* Since closure cannot be complete it must be strategic.  “Chose the kind of closure to apply to the design”.
* Conforming to OCP is expensive it takes development time and effort to create the appropriate abstractions.  Abstractions also increase complexity.  


### How do we manage abstraction?
* We initially write code expecting it to not change.  When a change occurs we implement abstraction to protect us from future change of that kind. - “Take the first bullet”
* Abstraction which is added to facilitate testing is likely to protect from change, SO TEST.
* Develop in short cycles
* Release often and early

---- 
## Liskov Substitution
http://en.wikipedia.org/wiki/Liskov_substitution_principle
Robert C. Martin, Chapter 10, Agile software development principles, patterns and practices, Pearson 2002
### Description
To define this principle Barbara Leskov wrote some stuff which I am stuffed if I can understand, look it up, repeat after me “WTF”, ignore it and read Bob Martin.

In general the principle proposes that “Subtypes must be substitutable for their base type”, in general think about what happens when you violate this principle.  If you have a function which takes a base class when a sub class is passed as a parameter the function misbehaves.

Consider the below two classes

	class Rectangle {
		int _width;
		int _height;
		
		public int getHeight() { return _height }
		
		public int area() { return _height * _width }
	}
	
	class Square extends Rectangle {
	
	}

But then we have to call the following to set the size of a square since the width and height are always the same.
* square.setWidth(10)
* square.setHeight(10)

So we refactor

	class Square extends Rectangle {
		public void setWidth(int width) {
			super.setWidth(width);
			super.setHeight(width);
		}
	}

Pretty slick until someone does this...

	public int modifyShapeAndGetArea(Rectangle r) {
		r.setWidth(10);
		return r.area();
	}
	 
	int area = modifyShapeAndGetArea(square);

The above method operates on the base class which is rectangle, thus it would not call the overridden methods you defined on square.  The class square does not comply with the LSP.

Ok simple refactoring, just make the methods virtual that way we can ensure that the subclasses methods are always called.

Nope still broken what if we do this...

	public int modifyShapeAndGetArea(Rectangle r, int height, int width) {
		r.setWidth(height);
		r.setWidth(width);
		return r.area();
	}
	
	int area = modifyShapeAndGetArea(square, 5, 4);
	assertEqual(20, area);

In our method we understand the behaviour of a rectangle therefore it is safe to assume that the above code would work. However we have subclassed Rectangle and changed the behaviour which causes Square to violate Rectangle.

* The LSP makes it clear that in OOD, the IS-A relationship pertains to behaviour that can be reasonably assumed and that clients depend on it.
* Most LSP violations are regarding derivative classes which remove functionality from their base classes.

---- 
## Dependency Inversion Principle
http://en.wikipedia.org/wiki/Dependency_inversion_principle
Robert C. Martin, Chapter 10, Agile software development principles, patterns and practices, Pearson 2002
### Description
* High level modules should not depend on low-level modules.  Both should depend on abstractions.
* Abstractions should not depend on details, details should depend on abstractions.
* Hollywood principle don’t call use we call you.  

### Depending on Abstractions
* No variable should hold a pointer or reference to a concrete class
* No class should derive from a concrete class
* No method should override an implemented method of any of its base class

![][image-1]

In the above example, Button no longer depends on a lamp but instead requests anything it is to control depends on the interface SwitchableDevice.

---- 
## Interface Segregation Principle
http://en.wikipedia.org/wiki/Interface_segregation_principle
Robert C. Martin, Chapter 11, Agile software development principles, patterns and practices, Pearson 2002
### Description
* This principle deals with the disadvantages of “fat” interfaces.  This means that the interface of the class can be broken up into groups of methods.
* Each group serves a different set of clients, some clients use one group some use others.
* The ISP suggests that a class only knows about interface methods which are relevant to it.  This saves the problem for clients having to provide implementation for a method that it has no use for.
* Separation also ensures that you only refactor the changes you are interested in, not because you are bound to a generic interface.

---- 
## STUPID

### Singleton
Why should you not use the singleton?
* Programs using global state are very difficult to test
* Programs that rely on global state hide their dependencies  


### Tight Coupling
If making a change in one module causes you to change another then coupling exists.  Tightly coupled modules are difficult to reuse and also hard to test.

### Untestability
Testing should not be hard, most of the time untestability is caused by tight coupling.

### Premature Optimisation
* Don’t do it
* (for experts) Don’t do it yet  


### Indescriptive Naming
* Name your classes, methods, attributes and variables properly
* Don’t abbreviate
* Write code for people not computers  


### Duplication
This is kind of self explanatory

---- 
## Design Smells
### Rigidity
The system is hard to change because every change forces many other changes to other parts of the system.

### Fragility
Changes cause the system to break in places that have no conceptual relationship to the part that was changed

### Immobility
It is hard to disentangle the system into components that can be reused in other systems.

### Viscosity
Doing things right is harder than doing things wrong.

### Needless Complexity
The design contains infrastructure that adds no direct benefit.

### Needless Repetition
The design contains repeating structures that could be unified under a single abstraction.

### Opacity
It is hard to read and understand.  It does not express its intent well.







[image-1]:	../../../../assets/images/inversion_principle.png