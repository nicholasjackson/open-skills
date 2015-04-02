# Techniques SOLID Explained

## Design Patterns

### The Mediator Pattern
http://en.wikipedia.org/wiki/Mediator_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/mediator
#### Description
Communication between objects is encapsulated by a mediator object.  Objects no longer communicate directly instead report their state to the mediator which is responsible to determine an action for another object.  This pattern not only reduces dependency and lowers the coupling between objects but allows the encapsulation of logic one central place.
#### Suggested Uses:
* Navigation

---- 
### The Observer Pattern
http://en.wikipedia.org/wiki/Observer_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/observer
#### Description
The observer pattern exists when an object called the subject maintains a list of dependents called observers.  When state changes in the subject it automatically notifies the observers of this change usually by calling one of their methods.
#### Suggested Uses:
* GUIs, used to connect buttons to controllers
* Models to notify a view of state change

---- 
### The Chain of Responsibility Pattern
http://en.wikipedia.org/wiki/Chain-of-responsibility_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/chain
#### Description
Where the observer pattern defines a one to many relationship for call to action the chain of responsibility implements tiered layers.  For example if you have a three tier application and the bottom layer is registered to respond to an event, if it can not deal with that event it will pass it on up the chain to its parent.  Should an element in the chain be able to respond to an event then it will do so and not pass the event any further up the chain.  Note events can propagate two ways it is possible for an object receiving an event to pass it up to a parent or down to a child.
#### Suggested Uses
* Event bubbling is a classic implementation of the Chain of Responsibility

---- 
### The Strategy Pattern
http://en.wikipedia.org/wiki/Strategy_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/strategy
#### Description
The strategy pattern says that you should extract the volatile parts of your code and encapsulate them as objects.  It allows you to maintain the volatile (parts that change often) code outside of your main application or select the implementation at runtime.  Rather than inherit or override a method in a base class all logic is encapsulated by an object which implements a common interface, you use polymorphism to choose the object you want to work with.
#### Suggested Uses
* You have volatile code that you can separate out of your application for easy maintenance
* You want to avoid muddling how you handle a task by having to split implementation code over several inherited classes
* You want to change the algorithm you use for a task at runtime

---- 
### The Decorator Pattern
http://en.wikipedia.org/wiki/Decorator_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/decorator
#### Description
The decorator patterns allows you to attach additional responsibilities to an object dynamically whilst maintaining the original objects interface.  Decorators provide a flexible alternative to subclassing which extends functionality at compile time unlike the decorator which extends at runtime.
#### Suggested Uses
* As an alternative to subclassing when you wish to extend the same functionality to multiple subtypes

---- 
### The Factory Pattern
http://en.wikipedia.org/wiki/Factory_method_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/abstract-factory
https://github.com/nicholasjackson/java-design-patterns/tree/master/factory-method
#### Description
In its simplest definition a factory is an object which creates other objects whose interface conforms to a common type. Generally there are two different types of factory pattern the abstract factory and the factory method.  The abstract factory generally has methods which return types which conform to a pre-determined family.  The factory method is used when the concrete return type may be unknown at design or compile time.  In both instances a factory should be defined as an abstract base class allowing the user to extend or override object creation as required.
#### Suggested Uses
* When the creation of an object is more complex than just calling the constructor
* When the resultant type is not known at compile time or could be user configurable

---- 
### The Singleton Pattern
http://en.wikipedia.org/wiki/Singleton_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/singleton
#### Description
The singleton pattern is a method of ensuring only one instance of a class is ever created.  It works by not allowing the end user access to the constructor of the class.  The only way to create an instance is to use a static method which controls the creation of the underlying object.  Remember when using a singleton the basic pattern is not thread safe, if using in a multithreaded read/write context then it may be necessary to implement more than the basic pattern.  When utilising the singleton pattern consider the two following factors:
* Programs using global state are very difficult to test
* Programs that rely on global state hide dependency
#### Suggested Uses
* Config or preferences

---- 
### The Flyweight Pattern
http://en.wikipedia.org/wiki/Flyweight_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/flyweight
#### Description
A flyweight is an object that minimises memory use by sharing as much data as possible with other objects.  To ensure thread safety objects stored within the flyweight are generally immutable.  Generally a Factory is used to create instances of flyweight objects and to cache them ensuring duplicate instances are never created.
#### Suggested Uses
* Where it may be expensive to create an instance of an object
* When multiple instances of the same object may consume large amounts of memory

---- 
### The Adapter Pattern
http://en.wikipedia.org/wiki/Adapter_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/adapter
#### Description
The adapter pattern allows two incompatible interfaces to work to work together.  The adapter encapsulates an object exposing a new interface without touching the source code of the existing object.
#### Suggested Uses
* Allowing an old object to work with a new interface
* Abstraction between presentation objects and an API model

---- 
### The Facade Pattern
http://en.wikipedia.org/wiki/Facade_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/facade
#### Description
Where the adapter allows two incompatible interfaces to work together the facade is all about simplifying an interface.  If you have an object with a complicated interface which requires calls to multiple methods in order to perform a function you may wish to re-write that interface.  In the instance that this is not possible you can use the facade pattern to wrap the old interface in a new simpler one. Note: this would wrap you code in one more level of abstraction do not use this when you can refactor the original code.
#### Suggested Uses
* When you wish to simplify an interface and can not modify the original code

---- 
### The Template Method
http://en.wikipedia.org/wiki/Template_method_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/template-method
#### Description
The template method is a behavioural design pattern it allows you to define the skeleton of an algorithm, deferring some steps to subclasses.  Subclasses can redefine certain steps in the algorithm without  changing the overall structure.  The base class defines abstract and virtual methods which are designed to be overridden by the subclass the method which controls the flow of the algorithm is never overridden this functionality is designed to be owned by the base class.
#### Suggested Uses
* Use as a method of factoring out common behaviour in library classes

---- 
### The Builder Pattern
http://en.wikipedia.org/wiki/Builder_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/builder
#### Description
The builder allows you to control the creation of a particular object.  Unlike an abstract factory where there is only one method to create and return an object the builder will provide minimal construction arguments then have several methods to set additional options.  Finally the user calls build to return an instance of the particular object.
#### Suggested Uses
* When you need to simplify the creation of an object by specifying a semantic interface (needs updated not too happy with this)

---- 
### The Iterator Pattern
http://en.wikipedia.org/wiki/Iterator_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/iterator
#### Description
The iterator pattern implements a standard way to loop over a collection of objects, the way the object stores the data internally is abstracted by the Iterable interface which is applied to the object.  It provides a way to access the elements of an aggregate object sequentially without exposing its underlying structure.
#### Suggested Uses
* When you have a custom container of objects implement the language default iterator interface to allow change to internal structure without affecting any consumer

---- 
### The Composite Pattern
http://en.wikipedia.org/wiki/Composite_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/composite
#### Description
The composite pattern allows you to treat all objects in a tree the same regardless if they are containers of objects or primitive objects.  This removes the requirements on the consuming class from having to perform a specific operation for each type.  The key to the Composite pattern is an abstract class that represents both primitives and their containers.
#### Suggested Uses
* You want to represent part-whole hierarchies of objects
* You want clients to be able to ignore the difference between compositions of objects and individual objects

---- 
### The State Pattern
http://en.wikipedia.org/wiki/State_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/state
#### Description
Allow an object to alter its behaviour when its internal state changes.  The object will appear to change its class.
#### Suggested Uses
* When you want to encapsulate

---- 
### The Proxy Pattern
http://en.wikipedia.org/wiki/Proxy_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/proxy
#### Description
The proxy pattern provides the interface of an object to local code without disclosing the origin.  The proxied object could be a remote object on the internet or it could be a local object and the proxy could be used to determine access. (NOTE: needs revision, not entirely happy with this description)
#### Suggested Uses
* Accessing remote objects
* Simplifying complex APIs
* Adding security access to an existing object

---- 
### The Command Pattern
http://en.wikipedia.org/wiki/Command_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/command
#### Description
The command pattern lets you package complex commands into a single object.  Rather than having to perform the multiple steps needed to execute each command every time.  Or in other words you are encapsulating a set of complex actions, targeted at a particular target into an easily handled object.  In its simplest use all commands extend an abstract command object which implements an interface for executing operations.  The executing class has no knowledge of the inner workings of the command it is only aware of the interface.  In the instance where a notification is required upon completion of the command a reference to a receiver is passed to the command, upon completion command calls the receiver.
#### Suggested Uses
* Implementing a menu, each menu item extends a base menu item the onclick of which executes a command
* Anywhere you have a complex sequence of commands you wish to abstract from the caller

---- 
### The Prototype Pattern
http://en.wikipedia.org/wiki/Prototype_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/prototype
#### Description
Similar to a factory pattern in that there is a class which is responsible for creating others with the exception that a new class is not created from scratch an existing implementation is cloned and then customised.
#### Suggested Uses
* When it takes a lot of resources, or a lot of code to create an object consider using the prototype pattern, copy an existing object and customise it instead

---- 
### The Bridge Pattern
http://en.wikipedia.org/wiki/Bridge_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/bridge
#### Description
The bridge pattern allows you to decouple an abstraction from its implementation so that the two can vary independently.
#### Suggested Uses
TODO: Need update, not sure i understand this one

---- 
### The Interpreter Pattern
http://en.wikipedia.org/wiki/Interpreter_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/interpreter
#### Description
Want to create you own programming language, thought not. This is not one of the most useful patterns, it is commonly used for creating an interpreter for an existing or new language.  Having said all that anyone up for writing an emoji based language let me know I will most likely be busy but there is a tiny tiny chance that insanity would have set in and I will agree.
#### Suggested Uses
* Create your own language
* Create a static code analysis tool

---- 
### The Memento Pattern
http://en.wikipedia.org/wiki/Memento_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/memento
#### Description
The memento pattern is about storing and restoring an particular objects state without violating the encapsulation of the containing object.  
#### Suggested Uses
* When you want to store a snapshot of an objects state for later restore
* A direct reference to obtaining the state would expose implementation details and break the object encapsulation

---- 
### The Visitor Pattern
http://en.wikipedia.org/wiki/Visitor_pattern
#### Code Example
https://github.com/nicholasjackson/java-design-patterns/tree/master/visitor
#### Description

#### Suggested Uses

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
#### Description
Polymorphism (from the Greek many form)  is the provision of a single interface to multiple entities.  It enables you to write code to perform various actions on an object but leaving the decision of what type of object to perform the action on implementation of that object to runtime.  Because multiple objects conform to the same interface they are interchangeable the compiler does not care that the object is of type A or B only that it has the interface Y.

---- 
### Inheritance
http://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming) 
#### Description
Inheritance is the ability of one object to inherit another’s properties and methods.  It is generally used when one class extends another implementing the base classes properties and methods and adding or overriding specific implementation of its own.  






