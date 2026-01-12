# Library Management System

A comprehensive library management system built with Java, demonstrating object-oriented programming principles. This console-based application allows librarians to manage books, borrowers, and lending operations efficiently.


## Features

### Book Management
- Add new books to the library (Paper books and E-books)
- Display all available books with their details
- Search functionality by title, author, or ISBN
- Track book availability status

### Borrower Management
- Register new borrowers with unique IDs
- View list of all registered borrowers
- Monitor books borrowed by each borrower

### Lending Operations
- Borrow books with automatic record creation
- Return borrowed books with timestamp tracking
- View complete borrowing history
- Prevent borrowing of already borrowed books

### User Interface
- Interactive console-based menu system
- Input validation and error handling
- Clear display of information and search results

## System Architecture

The project follows a layered architecture pattern with clear separation of concerns:

```
src/
├── models/          Layer for data models and entities
├── services/        Business logic and operations
├── utils/           Utility classes for console operations
└── Main.java        Application entry point
```

## OOP Concepts Applied

### Encapsulation
All class attributes are protected using access modifiers (private/protected) with public getter and setter methods providing controlled access to internal data.

### Inheritance
The Book class serves as an abstract base class, with PaperBook and EBook extending it. This demonstrates code reusability and hierarchical relationships.

### Abstraction
Abstract methods like getBookType() in the Book class force subclasses to provide their own implementations, hiding implementation details while exposing functionality.

### Polymorphism
Method overriding is used extensively. The toString() method is overridden in multiple classes, and getBookType() provides different implementations in PaperBook and EBook.

### Interface Implementation
The Searchable interface defines a contract for search operations, implemented by LibraryService to provide consistent search functionality.

## Prerequisites

- Java Development Kit (JDK) 8 or higher
- Any Java IDE (IntelliJ IDEA, Eclipse, NetBeans) or a text editor with command line
- Basic understanding of Java and OOP concepts





## Class Documentation

### Models Package

#### Book (Abstract Class)
Base class for all book types containing common attributes and methods.

**Attributes:**
- title: String - The book title
- author: String - The book author
- isbn: String - Unique book identifier
- isBorrowed: boolean - Availability status

**Key Methods:**
- getBookType(): Abstract method implemented by subclasses
- toString(): Returns formatted book information
- Getter and setter methods for all attributes

#### PaperBook
Represents physical books in the library.

**Additional Attributes:**
- pageCount: int - Number of pages in the book

**Implementation:**
- Extends Book class
- Implements getBookType() to return paper book information

#### EBook
Represents electronic books in the library.

**Additional Attributes:**
- fileFormat: String - Digital format (PDF, EPUB, etc.)

**Implementation:**
- Extends Book class
- Implements getBookType() to return e-book information

#### Borrower
Represents library members who can borrow books.

**Attributes:**
- id: String - Unique borrower identifier
- name: String - Borrower name
- borrowedBooks: List of BorrowRecord - Currently borrowed books

**Key Methods:**
- borrowBook(): Adds a borrow record
- returnBook(): Removes a borrow record
- toString(): Returns borrower information with book count

#### BorrowRecord
Tracks individual borrowing transactions.

**Attributes:**
- book: Book - The borrowed book
- borrower: Borrower - The borrowing member
- borrowDate: LocalDate - When the book was borrowed
- returnDate: LocalDate - When the book was returned (null if not returned)

**Key Methods:**
- markReturned(): Updates return date and book status
- toString(): Returns complete transaction information

### Services Package

#### LibraryService
Central service class managing all library operations.

**Attributes:**
- books: List of all books in the library
- borrowers: List of all registered borrowers
- borrowRecords: List of all borrowing transactions

**Key Methods:**
- addBook(): Registers a new book
- addBorrower(): Registers a new borrower
- borrowBook(): Processes a borrowing transaction
- searchByTitle/Author/Isbn(): Search operations
- getAllBooks/Borrowers/BorrowRecords(): Retrieval methods

#### Searchable (Interface)
Defines the contract for search operations.

**Methods:**
- searchByTitle(): Search books by title
- searchByAuthor(): Search books by author
- searchByIsbn(): Search books by ISBN

### Utils Package

#### ConsoleUtils
Provides utility methods for console input/output operations.

**Key Methods:**
- displayMenu(): Shows main menu options
- getIntInput(): Reads and validates integer input
- getStringInput(): Reads string input
- displayList(): Formats and displays lists
- pressToContinue(): Pauses for user acknowledgment

### Main Class

The entry point of the application that ties all components together. It initializes sample data and runs the main menu loop, handling user choices and coordinating between different services.

## Usage Guide

### Starting the Application

When you run the application, you will see the main menu with the following options:

```
==== Library Management System ====
1. Add New Book
2. Add New Borrower
3. Borrow a Book
4. Return a Book
5. Search Books
6. Display All Books
7. Display All Borrowers
8. Display Borrow Records
0. Exit
```

### Adding a Book

1. Select option 1 from the main menu
2. Enter the book title
3. Enter the author name
4. Enter the ISBN number
5. Choose book type (1 for Paper, 2 for E-Book)
6. For paper books, enter page count
7. For e-books, enter file format (PDF, EPUB, etc.)

### Adding a Borrower

1. Select option 2 from the main menu
2. Enter a unique borrower ID
3. Enter the borrower name

### Borrowing a Book

1. Select option 3 from the main menu
2. Enter the ISBN of the book to borrow
3. Enter the borrower ID
4. The system will create a borrow record if the book is available

### Returning a Book

1. Select option 4 from the main menu
2. Enter the ISBN of the book to return
3. The system will update the record and mark the book as available

### Searching for Books

1. Select option 5 from the main menu
2. Choose search type (Title, Author, or ISBN)
3. Enter your search term
4. View the search results

### Sample Data

The application comes with pre-loaded sample data:

**Books:**
- Java Programming by John Doe (ISBN: 1111111111) - Paper Book, 500 pages
- Python Basics by Jane Smith (ISBN: 2222222222) - E-Book, PDF format

**Borrowers:**
- Alice Johnson (ID: S1001)
- Bob Williams (ID: S1002)

## Future Enhancements

Potential improvements for the system:

- Database integration for persistent storage
- Due date tracking and late fee calculation
- Book reservation system
- User authentication and role-based access
- Email notifications for due dates
- Advanced reporting and statistics
- GUI interface using JavaFX or Swing
- Export functionality for reports
- Book rating and review system
- Multiple copies of the same book

## License

This project is created for educational purposes to demonstrate OOP concepts in Java.

## Contact

For questions or suggestions regarding this project, please create an issue in the repository.
