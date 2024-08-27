Here's a day-wise training plan for C++ development. This plan assumes a beginner to intermediate level of understanding and is structured over a two-week period. Each day will cover specific topics, with example code snippets to reinforce learning.

---

### **Week 1: Core C++ Fundamentals**

#### **Day 1: Introduction to C++ & Setting Up the Environment**
- **Topics:**
  - Introduction to C++ and its ecosystem.
  - Installing a C++ compiler and setting up an IDE (Visual Studio Code/Code::Blocks).
  - Writing your first C++ program.
- **Example Code:**
  ```cpp
  #include <iostream>

  int main() {
      std::cout << "Hello, World!" << std::endl;
      return 0;
  }
  ```

#### **Day 2: Basic Syntax & Variables**
- **Topics:**
  - Data types, variables, and constants.
  - Naming conventions.
  - Comments in C++.
- **Example Code:**
  ```cpp
  #include <iostream>

  int main() {
      int number = 10;
      std::string text = "Core C++";
      const double PI = 3.14159;

      std::cout << "Number: " << number << std::endl;
      std::cout << "Text: " << text << std::endl;
      std::cout << "PI: " << PI << std::endl;

      return 0;
  }
  ```

#### **Day 3: Operators & Expressions**
- **Topics:**
  - Arithmetic, relational, logical, and bitwise operators.
  - Expressions and operator precedence.
- **Example Code:**
  ```cpp
  #include <iostream>

  int main() {
      int a = 10, b = 20;
      int sum = a + b;
      bool isGreater = a > b;

      std::cout << "Sum: " << sum << std::endl;
      std::cout << "Is A greater than B? " << std::boolalpha << isGreater << std::endl;

      return 0;
  }
  ```

#### **Day 4: Control Statements**
- **Topics:**
  - If-else, switch-case.
  - Loops (for, while, do-while).
- **Example Code:**
  ```cpp
  #include <iostream>

  int main() {
      int number = 5;

      if (number > 0) {
          std::cout << "Positive" << std::endl;
      } else {
          std::cout << "Negative" << std::endl;
      }

      switch (number) {
          case 1:
              std::cout << "One" << std::endl;
              break;
          case 5:
              std::cout << "Five" << std::endl;
              break;
          default:
              std::cout << "Other" << std::endl;
      }

      for (int i = 1; i <= 5; i++) {
          std::cout << "Count: " << i << std::endl;
      }

      return 0;
  }
  ```

#### **Day 5: Arrays & Strings**
- **Topics:**
  - Introduction to arrays.
  - String handling (std::string class, methods).
- **Example Code:**
  ```cpp
  #include <iostream>
  #include <string>

  int main() {
      int numbers[] = {1, 2, 3, 4, 5};
      std::string text = "Core C++";

      for (int number : numbers) {
          std::cout << "Number: " << number << std::endl;
      }

      std::cout << "Length of text: " << text.length() << std::endl;
      std::cout << "Uppercase: " << text << std::endl;

      return 0;
  }
  ```

#### **Day 6: Functions & Recursion**
- **Topics:**
  - Function definition, parameters, and return types.
  - Recursion.
- **Example Code:**
  ```cpp
  #include <iostream>

  int factorial(int n) {
      if (n == 0) {
          return 1;
      } else {
          return n * factorial(n - 1);
      }
  }

  int main() {
      int result = factorial(5);
      std::cout << "Factorial of 5: " << result << std::endl;

      return 0;
  }
  ```

#### **Day 7: Object-Oriented Programming Basics**
- **Topics:**
  - Classes and objects.
  - Constructors.
  - Methods and encapsulation.
- **Example Code:**
  ```cpp
  #include <iostream>
  #include <string>

  class Car {
  private:
      std::string model;
      int year;

  public:
      // Constructor
      Car(std::string model, int year) {
          this->model = model;
          this->year = year;
      }

      // Method
      void displayInfo() {
          std::cout << "Model: " << model << ", Year: " << year << std::endl;
      }
  };

  int main() {
      Car car("Toyota", 2022);
      car.displayInfo();

      return 0;
  }
  ```

---

### **Week 2: Advanced Core C++**

#### **Day 8: Inheritance & Polymorphism**
- **Topics:**
  - Inheritance.
  - Method overriding.
  - Polymorphism.
- **Example Code:**
  ```cpp
  #include <iostream>

  class Animal {
  public:
      virtual void sound() {
          std::cout << "Animal makes a sound" << std::endl;
      }
  };

  class Dog : public Animal {
  public:
      void sound() override {
          std::cout << "Dog barks" << std::endl;
      }
  };

  int main() {
      Animal* myDog = new Dog();
      myDog->sound(); // Polymorphism

      delete myDog;
      return 0;
  }
  ```

#### **Day 9: Abstraction & Interfaces (Pure Virtual Functions)**
- **Topics:**
  - Abstract classes and methods (pure virtual functions).
  - Interfaces (abstract base classes).
- **Example Code:**
  ```cpp
  #include <iostream>

  class Animal {
  public:
      virtual void sound() = 0; // Pure virtual function
  };

  class Dog : public Animal {
  public:
      void sound() override {
          std::cout << "Dog barks" << std::endl;
      }
  };

  int main() {
      Animal* myDog = new Dog();
      myDog->sound();

      delete myDog;
      return 0;
  }
  ```

#### **Day 10: Exception Handling**
- **Topics:**
  - Try-catch blocks.
  - Throwing exceptions.
  - Custom exceptions.
- **Example Code:**
  ```cpp
  #include <iostream>
  #include <stdexcept>

  int divide(int a, int b) {
      if (b == 0) {
          throw std::runtime_error("Division by zero");
      }
      return a / b;
  }

  int main() {
      try {
          int result = divide(10, 0);
          std::cout << "Result: " << result << std::endl;
      } catch (const std::runtime_error& e) {
          std::cout << "Error: " << e.what() << std::endl;
      }

      return 0;
  }
  ```

#### **Day 11: STL - Vectors, Sets, and Maps**
- **Topics:**
  - Introduction to the Standard Template Library (STL).
  - Vectors, sets, and maps.
- **Example Code:**
  ```cpp
  #include <iostream>
  #include <vector>
  #include <set>
  #include <map>

  int main() {
      // Vector Example
      std::vector<std::string> list = {"C++", "Python"};
      for (const auto& item : list) {
          std::cout << "List item: " << item << std::endl;
      }

      // Set Example
      std::set<std::string> set = {"C++", "C++"}; // Duplicate won't be added
      for (const auto& item : set) {
          std::cout << "Set item: " << item << std::endl;
      }

      // Map Example
      std::map<std::string, int> map = {{"C++", 1}, {"Python", 2}};
      for (const auto& pair : map) {
          std::cout << "Map key: " << pair.first << ", value: " << pair.second << std::endl;
      }

      return 0;
  }
  ```

#### **Day 12: File Handling**
- **Topics:**
  - Reading and writing files using `fstream`.
  - Basic file operations (open, read, write, close).
- **Example Code:**
  ```cpp
  #include <iostream>
  #include <fstream>
  #include <string>

  int main() {
      // Writing to a file
      std::ofstream outFile("example.txt");
      outFile << "Hello, File Handling!" << std::endl;
      outFile.close();

      // Reading from a file
      std::ifstream inFile("example.txt");
      std::string line;
      while (std::getline(inFile, line)) {
          std::cout << line << std::endl;
      }
      inFile.close();

      return 0;
  }
  ``

