
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

