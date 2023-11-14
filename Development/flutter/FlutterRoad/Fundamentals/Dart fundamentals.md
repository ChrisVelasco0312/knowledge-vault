
# Variables

Using the keyword `var` we can initialize a variable that infers type.
You can change the type by specifying it.
Use `var` for local variables rather than type annotations.

"The Dart language enforces sound null safety.": Meaning that in Dart, the system helps prevent errors related to "null" values. The language has built-in features that make it less likely for your program to encounter unexpected crashes or errors caused by trying to use values that are not properly defined (null.)  [[Null safety Coming from JS]]

```dart
String? name // Nullable type
String name // Non-nullable type
```

- You must initialize variables before using them.
- Nullable variables are initialized by default with `null`
- Method calls on an expression with a nullable type can not be accessed.
## const and final

Use if you never intend to change a variable. A final variable can be set only once; a const variable is a compile time constant.

Use const for variables that you want to be compile-time constants.
The const keyword can also be used to create constant values. Any variable can have constant value.  [[Compile and Run Time]]


# Classes

Are the fundamental building blocks of (OOP).
Allows to create custom data types (objects).
Dart follows class-based and mixin-based inheritances, which is more similar to traditional object-oriented programming languages. Classes are used to defined blueprints for **objects**, and object are instances of those classes.
All classes except Null descent from Object

## Class declaration

Use the `class` keyword, followed by the name of the class. Class names start with uppercase letter

```dart
class Person {
	// class member will be defined here
}
```

## Properties (instance variables)

Properties are variables that hold data related to the class.
Represent the characteristics or attributes of the objects created from the class.

```dart
class Person {
	String name;
	int age;
}
```

## Constructor 

Is a special method used to create objects from the class. Initializes the properties of the object when it is instantiated.

```dart
class Person {
	String name;
	int age;

	// Constructor
	Person(this.name, this.age);
}
```

## Methods (member functions)

Are functions defined within the class. They represent the behavior or actions that the objects can perform.

```dart
class Person {
	String name;
	int age;

	Person(this.name, this.age);

	void sayHello() {
		print('Hello, my name is $name and I am $age years old.');	
	}
}
```

## Creating objects (instances)

To use a class, you create instances from it. You can do this by calling the constructor of the class

```dart
void main() {
  // Creating an object from the Person class
  var person = Person('John', 30);
  
  // Calling the method on the object
  person.sayHello(); // Output: Hello, my name is John and I am 30 years old.
}
```

## Inheritance

Allows to create a new class based on an existing class.
The new class inherits the properties and methods of the base class, and you can override or extend them as needed:

```dart
class Student extends Person {
	String school;

	//constructor
	Student(String name, int age, this.school) : super(name, age);

	@override
	void sayHello() {
		print('Hello, my name is $name, I am $age years old, and I study at $school.');
	}
}
```


**Why constructors are not inherited from a superclass?** _[[A note about constructors and inheritance]]_

## Asynchronous programming

### `Future` in Dart:

A `Future` represents a potential value or error that will be available at some point in the future. It's use to handle asynchronous operations and is commonly used for one-time computations.

```dart
Future<T> functionName() { 
	// Asynchronous code that computes a value of type T 
}
```

You can create a `Future` using the `Future` constructor or by using factor functions like `Future.value()` and `Future.delayed()`

### `Stream` in Dart:

A `Stream` is a sequence of asynchronous events. It's used to represent a continuous flow of data over time. Streams are suitable for handling multiple asynchronous events or values.

```dart
Stream<T> functionName() async* {
  // Asynchronous code that yields values of type T using the yield keyword
}
```

A `Stream` allows you to work with data as it arrives, rather than waiting for all the data to be available at once. 

#### `async*` and `yield`

The `async*` keyword is used to define a generator function that produces a `Stream`. The asterisk `*` indicates that the function uses the `yield` keyword to emit multiple values over time.

The `yield` keyword is uses within a `async*` function to emit values to the associated steam. It allows you to pause the function's execution and send a value to the stream. When the stream's consumer (listener) reads the emitted value, the generator function resumes execution from where it was paused by the previous `yield` statement.


