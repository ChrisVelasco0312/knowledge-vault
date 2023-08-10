Flutter fundamentals

Compile and Run Time

**Compile Time:**
Compile time refers to the phase when your code is being converted from human-readable source code into machine-readable instructions. This happens before your program actually runs. During compile time, the compiler checks your code for syntax errors, optimizes it, and prepares it for execution.

**Example:**
Imagine you're writing a letter. Compile time is like proofreading and organizing your letter before you send it. You fix any grammar mistakes and arrange the sentences nicely so that the reader can understand it easily. This preparation is done before the reader actually starts reading the letter.

**Runtime:**
Runtime refers to the phase when your compiled code is executed and runs on the computer or device. It's the time when your program is actively doing what you designed it to do. Runtime involves interacting with memory, performing calculations, and responding to user inputs.

**Example:**
Using the same letter analogy, runtime is when the reader actually reads the letter and understands its contents. They might react to what's written in the letter by taking actions, like responding to your requests or questions. This is the time when the content of the letter has a real impact.

**Putting It Together with an Example:**
Let's consider a simple Dart program that calculates the area of a rectangle:

```dart
void main() {
  final int length = 5; // Compile time: variable declaration
  final int width = 3;  // Compile time: variable declaration
  final int area = length * width; // Compile time: calculation
  
  print("The area of the rectangle is $area"); // Runtime: printing
}
```

- During compile time, the Dart compiler checks the syntax of your code, verifies that variable types match, and calculates the result of `length * width`. It ensures that your code is ready to be executed.
- At runtime, when you run the program, the calculated area value is used to print the message. The computer does the multiplication, retrieves the values of `length` and `width`, and generates the output based on those values.

In summary, compile time is about preparing your code for execution, like proofreading and organizing a letter before sending it. Runtime is when the program is actively running and performing the tasks you programmed it to do, like the reader actually reading and reacting to the letter's content.