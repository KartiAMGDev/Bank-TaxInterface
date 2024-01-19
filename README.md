# Bank-TaxInterface
﻿

Management System
1.Design a Java program that uses OOP principles to model the Book Create two classes: Book and Library. The Book class should have attributes such as bookID, title, author, and isAvailable. The Library class should include an array to store book objects.
2.Provide methods to add book, remove book search book (using id) and display books.
Write a Java program that demonstrates the use of these classes and methods by allowing the user to interact with the library system.

class Book{
//attributes
// Constructor to initialize book attributes
// Getter and setter methods for book attributes
}

class Library
private Book[] books
public library(){
this.books = new Book[5];}

// Method to add a book to the library
public void addBook Book book){

// Add the book to the books Array
}
//Method to replace a book from the library
public void replaceBookfint bookID) {
// replace the book name and author of the given bookiD from the
books}
// Method to display all books in the library
public void displayBooks(){}}

public class BookManagementSystem 
{public static void main(String[] args) { Library library=new Library():
Implement a menu-driven user interface to interact with the library system
// Allow users to add, replace and display books}}

Program starts from here :
import java.util.Scanner;

class Book {
    private int bookID;
    private String title;
    private String author;
    private boolean isAvailable;

    public Book(int bookID, String title, String author) {
        this.bookID = bookID;
        this.title = title;
        this.author = author;
        this.isAvailable = true;
    }

    // Getter and setter methods
    public int getBookID() {
        return bookID;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public boolean isAvailable() {
        return isAvailable;
    }

    public void setAvailable(boolean available) {
        isAvailable = available;
    }
}

class Library {
    private Book[] books;

    public Library() {
        this.books = new Book[5];
    }

    // Method to add a book to the library
    public void addBook(Book book) {
        for (int i = 0; i < books.length; i++) {
            if (books[i] == null) {
                books[i] = book;
                System.out.println("Book added successfully.");
                return;
            }
        }
        System.out.println("Library is full. Cannot add more books.");
    }

    // Method to replace a book in the library
    public void replaceBook(int bookID, String newTitle, String newAuthor) {
        for (int i = 0; i < books.length; i++) {
            if (books[i] != null && books[i].getBookID() == bookID) {
                books[i].setTitle(newTitle);
                books[i].setAuthor(newAuthor);
                System.out.println("Book replaced successfully.");
                return;
            }
        }
        System.out.println("Book not found with ID " + bookID);
    }

    // Method to display all books in the library
    public void displayBooks() {
        System.out.println("Books in the library:");
        for (Book book : books) {
            if (book != null) {
                System.out.println("Book ID: " + book.getBookID());
                System.out.println("Title: " + book.getTitle());
                System.out.println("Author: " + book.getAuthor());
                System.out.println("Available: " + (book.isAvailable() ? "Yes" : "No"));
                System.out.println("----------------------------");
            }
        }
    }
}

public class BookManagementSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Library library = new Library();

        int choice;
        do {
            System.out.println("Book Management System");
            System.out.println("1. Add Book");
            System.out.println("2. Replace Book");
            System.out.println("3. Display Books");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter Book ID: ");
                    int bookID = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter Title: ");
                    String title = scanner.nextLine();
                    System.out.print("Enter Author: ");
                    String author = scanner.nextLine();

                    Book newBook = new Book(bookID, title, author);
                    library.addBook(newBook);
                    break;

                case 2:
                    System.out.print("Enter Book ID to replace: ");
                    int replaceBookID = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter new Title: ");
                    String newTitle = scanner.nextLine();
                    System.out.print("Enter new Author: ");
                    String newAuthor = scanner.nextLine();

                    library.replaceBook(replaceBookID, newTitle, newAuthor);
                    break;

                case 3:
                    library.displayBooks();
                    break;

                case 4:
                    System.out.println("Exiting Book Management System. Goodbye!");
                    break;

                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        } while (choice != 4);

        scanner.close();
    }
}

2)﻿Create Interface Taxable with members sales Tax=7% and income Tax-10.5%. create abstract method calc Tax().
a. Create class Employee(empld.name.salary) and implement Taxable to calculate income Tax on yearly salary.
b. Create class Product(pid, price,quantity) and implement Taxable to calculate sales Tax on unit price of product.
c. Create class for main method(Say XYZ), accept employee information and a product information from user and print income tax and sales tax respectively

import java.util.Scanner;

// Taxable interface
interface Taxable {
    double salesTax = 0.07;   // 7% sales tax
    double incomeTax = 0.105; // 10.5% income tax

    // Abstract method to calculate tax
    double calcTax();
}

// Employee class implementing Taxable interface
class Employee implements Taxable {
    private int empId;
    private String name;
    private double salary;

    // Parameterized constructor
    public Employee(int empId, String name, double salary) {
        this.empId = empId;
        this.name = name;
        this.salary = salary;
    }

    // Implementation of calcTax() for income tax calculation
    @Override
    public double calcTax() {
        return salary * incomeTax;
    }
}

// Product class implementing Taxable interface
class Product implements Taxable {
    private int productId;
    private double price;
    private int quantity;

    // Parameterized constructor
    public Product(int productId, double price, int quantity) {
        this.productId = productId;
        this.price = price;
        this.quantity = quantity;
    }

    // Implementation of calcTax() for sales tax calculation
    @Override
    public double calcTax() {
        return price * salesTax * quantity;
    }
}

// Main class XYZ
public class XYZ {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Accept employee information
        System.out.print("Enter Employee ID: ");
        int empId = scanner.nextInt();
        scanner.nextLine(); // Consume newline
        System.out.print("Enter Employee Name: ");
        String empName = scanner.nextLine();
        System.out.print("Enter Employee Salary: ");
        double empSalary = scanner.nextDouble();

        // Create Employee object and calculate income tax
        Employee employee = new Employee(empId, empName, empSalary);
        double incomeTax = employee.calcTax();
        System.out.println("Income Tax for Employee: $" + incomeTax);

        // Accept product information
        System.out.print("Enter Product ID: ");
        int productId = scanner.nextInt();
        System.out.print("Enter Product Price: ");
        double productPrice = scanner.nextDouble();
        System.out.print("Enter Product Quantity: ");
        int productQuantity = scanner.nextInt();

        // Create Product object and calculate sales tax
        Product product = new Product(productId, productPrice, productQuantity);
        double salesTax = product.calcTax();
        System.out.println("Sales Tax for Product: $" + salesTax);

        // Close the scanner
        scanner.close();
    }
}

