### **Week 3: Project Development - Library Management System**

Now that you've covered the fundamental and advanced concepts, let's implement a console-based "Library Management System" similar to the Java version but in C++.

#### **Project: Library Management System**

#### **Project Overview:**
- **Features:**
  1. Add a new book to the library.
  2. Issue a book to a user.
  3. Return a book.
  4. Display all books.
  5. Save and load book data from a file.

#### **Step 1: Define Classes**

- **Book Class:**
  - Represents a book in the library.
  - Contains attributes like title, author, and availability status.
  
- **Library Class:**
  - Manages the collection of books.
  - Provides methods to add, issue, return, and display books.

#### **Book.h**
```cpp
#ifndef BOOK_H
#define BOOK_H

#include <string>

class Book {
private:
    std::string title;
    std::string author;
    bool isIssued;

public:
    // Constructor
    Book(const std::string& title, const std::string& author);

    // Getters
    std::string getTitle() const;
    std::string getAuthor() const;
    bool getIsIssued() const;

    // Issue and return the book
    void issueBook();
    void returnBook();

    // Display book details
    void display() const;
};

#endif
```

#### **Book.cpp**
```cpp
#include "Book.h"
#include <iostream>

// Constructor
Book::Book(const std::string& title, const std::string& author) 
    : title(title), author(author), isIssued(false) {}

// Getters
std::string Book::getTitle() const { return title; }
std::string Book::getAuthor() const { return author; }
bool Book::getIsIssued() const { return isIssued; }

// Issue the book
void Book::issueBook() {
    if (!isIssued) {
        isIssued = true;
        std::cout << "Book issued successfully!" << std::endl;
    } else {
        std::cout << "Book is already issued." << std::endl;
    }
}

// Return the book
void Book::returnBook() {
    if (isIssued) {
        isIssued = false;
        std::cout << "Book returned successfully!" << std::endl;
    } else {
        std::cout << "Book was not issued." << std::endl;
    }
}

// Display book details
void Book::display() const {
    std::cout << "Title: " << title << ", Author: " << author 
              << ", Issued: " << std::boolalpha << isIssued << std::endl;
}
```

#### **Library.h**
```cpp
#ifndef LIBRARY_H
#define LIBRARY_H

#include "Book.h"
#include <vector>
#include <string>

class Library {
private:
    std::vector<Book> books;

public:
    // Methods to manage books
    void addBook(const Book& book);
    void issueBook(const std::string& title);
    void returnBook(const std::string& title);
    void displayBooks() const;

    // File handling methods
    void saveBooks() const;
    void loadBooks();
};

#endif
```

#### **Library.cpp**
```cpp
#include "Library.h"
#include <iostream>
#include <fstream>

// Add a new book to the library
void Library::addBook(const Book& book) {
    books.push_back(book);
    std::cout << "Book added successfully!" << std::endl;
}

// Issue a book
void Library::issueBook(const std::string& title) {
    for (Book& book : books) {
        if (book.getTitle() == title) {
            book.issueBook();
            return;
        }
    }
    std::cout << "Book not found." << std::endl;
}

// Return a book
void Library::returnBook(const std::string& title) {
    for (Book& book : books) {
        if (book.getTitle() == title) {
            book.returnBook();
            return;
        }
    }
    std::cout << "Book not found." << std::endl;
}

// Display all books
void Library::displayBooks() const {
    if (books.empty()) {
        std::cout << "No books in the library." << std::endl;
    } else {
        for (const Book& book : books) {
            book.display();
        }
    }
}

// Save the books to a file
void Library::saveBooks() const {
    std::ofstream outFile("books.dat", std::ios::binary);
    if (outFile) {
        for (const Book& book : books) {
            outFile.write((char*)&book, sizeof(Book));
        }
        std::cout << "Books saved successfully!" << std::endl;
    } else {
        std::cout << "Error saving books." << std::endl;
    }
    outFile.close();
}

// Load the books from a file
void Library::loadBooks() {
    std::ifstream inFile("books.dat", std::ios::binary);
    if (inFile) {
        books.clear();
        Book book("", "");
        while (inFile.read((char*)&book, sizeof(Book))) {
            books.push_back(book);
        }
        std::cout << "Books loaded successfully!" << std::endl;
    } else {
        std::cout << "Error loading books." << std::endl;
    }
    inFile.close();
}
```

#### **main.cpp**
```cpp
#include "Library.h"
#include <iostream>

int main() {
    Library library;
    int choice;
    std::string title, author;

    do {
        std::cout << "\nLibrary Management System\n";
        std::cout << "1. Add Book\n";
        std::cout << "2. Issue Book\n";
        std::cout << "3. Return Book\n";
        std::cout << "4. Display Books\n";
        std::cout << "5. Save Books\n";
        std::cout << "6. Load Books\n";
        std::cout << "7. Exit\n";
        std::cout << "Enter your choice: ";
        std::cin >> choice;
        std::cin.ignore();

        switch (choice) {
            case 1:
                std::cout << "Enter book title: ";
                std::getline(std::cin, title);
                std::cout << "Enter book author: ";
                std::getline(std::cin, author);
                library.addBook(Book(title, author));
                break;
            case 2:
                std::cout << "Enter book title to issue: ";
                std::getline(std::cin, title);
                library.issueBook(title);
                break;
            case 3:
                std::cout << "Enter book title to return: ";
                std::getline(std::cin, title);
                library.returnBook(title);
                break;
            case 4:
                library.displayBooks();
                break;
            case 5:
                library.saveBooks();
                break;
            case 6:
                library.loadBooks();
                break;
            case 7:
                std::cout << "Exiting system. Goodbye!\n";
                break;
            default:
                std::cout << "Invalid choice. Please try again.\n";
        }
    } while (choice != 7);

    return 0;
}
```

### **Explanation:**
1. **Book Class:** Represents each book with attributes like `title`, `author`, and `isIssued`. It provides methods to issue and return the book, along with a method to display the book's details.

2. **Library Class:** Manages a collection of books using a `std::vector`. It includes methods to add, issue, return, and display books. It also handles saving and loading books from a binary file.

3. **Main Function:** The main function provides a menu-driven interface that allows the user to interact with the library system by adding, issuing, returning, displaying,
